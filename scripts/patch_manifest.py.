import re

path = "android/app/src/main/AndroidManifest.xml"
with open(path, encoding="utf-8") as f:
    content = f.read()

perms = [
    '<uses-permission android:name="android.permission.SCHEDULE_EXACT_ALARM" />',
    '<uses-permission android:name="android.permission.USE_EXACT_ALARM" />',
    '<uses-permission android:name="android.permission.POST_NOTIFICATIONS" />',
]
missing = [p for p in perms if p.split('"')[1] not in content]
if missing:
    content = re.sub(r'(<manifest[^>]*>)', r'\1\n    ' + '\n    '.join(missing), content, count=1)
    with open(path, "w", encoding="utf-8") as f:
        f.write(content)
    print("Added permissions:", missing)
else:
    print("Permissions already present.")
