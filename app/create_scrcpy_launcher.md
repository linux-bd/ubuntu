### Create Scrcpy Launcher
```sh
#!/bin/bash

# Set variables
APP_DIR="/opt/apps/Scrcpy"
ICON_PATH="$HOME/.local/share/icons/scrcpy.png"
DESKTOP_FILE="$HOME/.local/share/applications/scrcpy.desktop"

# Copy icon to user's icon directory
mkdir -p "$(dirname "$ICON_PATH")"
cp "$APP_DIR/icon.png" "$ICON_PATH"

# Create .desktop launcher
cat > "$DESKTOP_FILE" <<EOF
[Desktop Entry]
Name=Scrcpy
Comment=Display and control Android devices
Exec=$APP_DIR/scrcpy
Icon=scrcpy
Terminal=false
Type=Application
Categories=Utility;
EOF

# Make the launcher executable
chmod +x "$DESKTOP_FILE"

# Optional: Copy to Desktop
cp "$DESKTOP_FILE" "$HOME/Desktop/"
chmod +x "$HOME/Desktop/scrcpy.desktop"

echo "✅ Scrcpy launcher created successfully."
echo "➡️ You can find it in your applications menu or on your desktop."
echo "🖱️ Right-click the desktop icon and select 'Allow Launching' if needed."
```
