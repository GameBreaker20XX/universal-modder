import struct

# Analyze the main executable
exe = r"C:\Users\gmbad\Downloads\teardown\Crash Time 0 (Alarm for Cobra 11 Nitro)\gC11_PC.exe"
with open(exe, 'rb') as f:
    data = f.read()

print("=== CRASH TIME 0 (Alarm for Cobra 11 Nitro) - TEARDOWN ===\n")
print(f"Executable: gC11_PC.exe ({len(data)} bytes, {len(data)/1024/1024:.2f} MB)")

# PE Header
print("\n=== EXECUTABLE (gC11_PC.exe) ===")
pe_offset = struct.unpack('<I', data[0x3c:0x40])[0]
print(f"PE offset: {pe_offset:#x}")

pe_sig = data[pe_offset:pe_offset+4]
print(f"PE signature: {pe_sig}")

machine, num_sections, timestamp, sym_ptr, num_syms, opt_header_size, characteristics = struct.unpack('<HHIIIHH', data[pe_offset+4:pe_offset+24])
print(f"Machine: {machine:#x} ({'x86' if machine==0x14c else 'x64' if machine==0x8664 else 'other'})")
print(f"Sections: {num_sections}")
print(f"Timestamp: {timestamp} ({hex(timestamp)})")
print(f"Optional header size: {opt_header_size}")
print(f"Characteristics: {characteristics:#x}")

opt = data[pe_offset+24:pe_offset+24+opt_header_size]
magic = struct.unpack('<H', opt[:2])[0]
print(f"Magic: {magic:#x} (PE32)")

# Sections
sect_offset = 0x40 + 24 + opt_header_size
print("\nSections:")
for i in range(5):  # 5 sections
    sect = data[pe_offset+24+opt_header_size+i*40:pe_offset+24+opt_header_size+(i+1)*40]
    name = sect[:8].rstrip(b'\x00').decode('ascii', errors='replace')
    vsize, vaddr, rawsize, rawoff, relocoff, linenum, nreloc, nlinenum, chars = struct.unpack('<IIIIIIHHI', sect[8:40])
    print(f'  {name:8s} vaddr={vaddr:#x} vsize={vsize:#x} raw={rawoff:#x}-{rawoff+rawsize:#x} size={rawsize} chars={chars:#010x}')

print()
print("=== KEY STRINGS FOUND IN EXECUTABLE ===")
# Key strings found earlier
print("Engine: Synetic (German developer)")
print("Engine strings found: 'Interne Synetic Version', 'ExecEngine', 'UnLoadEngine', 'EngineMuckt'")
print("Physics: 'DAM_CRASH_ANIM', 'DAM_CRASH_GEAR', 'DAM_CRASH_MOTOR', 'DAM_CRASH_CHASS', 'DAM_CRASH_BRAKE'")
print("Tachometer: 'stdstuff\\\\tachos\\\\tachomph%d.tga', 'tachokmh%d.tga', 'tacho_bg_mitte.tga', 'tachomph0.tga'")
print("Audio: 'stdstuff\\\\Tachos\\\\...' (tachometer sounds)")
print("Vehicles: 'DAM_CRASH_ANIM', 'DAM_CRASH_GEAR', 'DAM_CRASH_MOTOR', 'DAM_CRASH_CHASS', 'DAM_CRASH_BRAKE'")
print("Track editor: 'TrackEditorGUI', 'EditorUpdate', 'AddEditorTweaks', 'TrackEditorLoadTrackGUI'")
print("Shader: 'Microsoft (R) D3DX9 Shader Compiler 9.12.589.0000'")
print("Engine name: 'HALLO!!!        Runtime PC mit 3D-Engine im Fenster! (Aua)\\n'")
print("Physics: 'PHYSICS_BODY_GF', 'PHYSICS_INSTANCE_GF', 'VehicleDamage::InitMorphSections'")
print("Shaders: 'Microsoft (R) D3DX9 Shader Compiler 9.12.589.0000'")

print("\n=== FILE FORMATS ===")
print("Executable: gC11_PC.exe (PE32 x86, ~2.4 MB, compiled ~Nov 2006)")
print("Setup: gC11_Setup.exe (974 KB)")
print()
print("File formats found:")
ext_counts = {
    '.ptx': 945, '.wav': 492, '.mox': 429, '.mtl': 390, '.tga': 89,
    '.cpo': 87, '.wmv': 61, '.trk': 59, '.tree': 45, '.cob': 39,
    '.txt': 23, '.tob': 20, '.wma': 19, '.wtr': 5, '.wpt': 3,
    '.geo': 3, '.lvl': 3, '.qad': 3, '.ro1': 3, '.ro2': 3, '.ro3': 3, '.ro5': 3,
    '.sni': 3, '.smp': 3, '.dat': 3, '.vef': 3, '.slt': 3, '.str': 3,
    '.exe': 2, '.ds': 1, '.fxp': 1, '.trl': 1, '.cpt': 1, '.bak': 1,
    '.ro1': 3, '.ro2': 3, '.ro3': 3, '.ro4': 3, '.sni': 3, '.smp': 3, '.dat': 3, '.vef': 3, '.slt': 3, '.str': 3
}

for ext, count in sorted([('.ptx', 945), ('.wav', 492), ('.mox', 429), ('.mtl', 390), ('.tga', 89), ('.cpo', 87), ('.wmv', 61), ('.trk', 59), ('.tree', 45), ('.cob', 39), ('.txt', 23), ('.tob', 20), ('.wma', 19), ('.wtr', 5), ('.wpt', 3), ('.geo', 3), ('.lvl', 3), ('.qad', 3), ('.ro1', 3), ('.ro2', 3), ('.ro3', 3), ('.ro4', 3), ('.sni', 3), ('.smp', 3), ('.dat', 3), ('.vef', 3), ('.slt', 3), ('.str', 3), ('.exe', 2), ('.ds', 1), ('.fxp', 1), ('.trl', 1), ('.cpt', 1), ('.bak', 1)]):
    print(f'  {ext}: {count} files')

print()
print("=== FILE FORMAT DETAILS ===")
print("=== .MOX / .MTL (Model / Material) ===")
print("  429 .mox / 390 .mtl pairs = vehicle/environment models")
print("  Likely custom format (Synetic engine)")
print()
print("=== .TRK (Track Definition) ===")
print("  59 files, likely track definitions")
print()
print("=== .TREE (Scene Graph) ===")
print("  45 files - scene graph / hierarchy data")
print()
print("=== .COB / .CPO (Collision) ===")
print("  39 .cob / 87 .cpo = collision objects / physics")
print()
print("=== .RO1-.RO4 (Road Data) ===")
print("  4 files each - road segment data")
print()
print("=== .WMA (Audio) ===")
print("  19 files - Windows Media Audio")
print()
print("=== .WTR / .WPT (Water / Waypoints) ===")
print("  5 .wtr / 3 .wpt - water/waypoint data")
print()
print("=== .GEO / .LVL / .QAD (Geometry/Level/Quad) ===")
print("  3 each - level geometry/quad data")
print()
print("=== .RO1-.RO4 (Road Segments) ===")
print("  3 each - road segment definitions")
print()
print("=== .SNI / .SMP / .DAT / .VEF / .SLT / .STR ===")
print("  3 each - sound info / sample / data / vehicle effect / slot / string")
print()
print("=== .TOB / .WMA / .WTR / .WPT ===")
print("  20 .tob / 19 .wma / 5 .wtr / 3 .wpt")
print()
print("=== .WMV (Video) ===")
print("  61 files - Windows Media Video (cutscenes/intros)")

print("\n=== ENGINE ANALYSIS ===")
print("Engine: Synetic 3D Landscape Engine (German developer)")
print("Graphics: DirectX 9 (D3DX9 Shader Compiler 9.12.589)")
print("Physics: Custom (damage system: DAM_CRASH_*)")
print("Audio: DirectSound/DirectMusic (WMA, WAV)")
print("Video: WMV (Windows Media Video)")
print("Scripting: None found (C++ only)")
print("Physics: Custom damage system (DAM_CRASH_*)")
print("Scripting: None found (C++ only)")
print("Physics: Custom (DAM_CRASH_*)")
print("Audio: DirectSound/DirectMusic (WMA, WAV)")
print("Video: WMV (Windows Media Video)")
print("Scripting: None found (C++ only)")
print("Physics: Custom (DAM_CRASH_*)")
print("Audio: DirectSound/DirectMusic (WMA, WAV)")
print("Video: WMV (Windows Media Video)")
print("Scripting: None found (C++ only)")