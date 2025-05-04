#!/bin/bash

# Define spinner frames (custom emoji spinner)
spinner_icons=( "🚀" "🛠️" "📦" "📥" "🧩" "🔧" "📦" "⚙️" "🖥️" )

# Spinner function
spinner() {
    local pid=$1
    local delay=0.2
    local i=0
    local n=${#spinner_icons[@]}
    while kill -0 $pid 2>/dev/null; do
        printf "\r[%s] Installing Yet Another Dialog (YAD)..." "${spinner_icons[i]}"
        i=$(( (i+1) % n ))
        sleep $delay
    done
    printf "\r[✅] Installation step complete!            \n"
}

# Update package list
sudo apt-get update

# Install required dependencies
sudo apt-get -y install libwebkit2gtk-4.0-dev auto-tools intltoolize libgspell-1 libwebkit2gtk-4.0-dev gir1.2-gspell-1 libdbus-glib2.0-cil-dev
sudo apt-get -y install automake build-essential intltool libglib2.0-dev libgtk-3-dev libglib2.0-dev libgtk-3-dev gcc libglib2.0-dev-bin intltool
sudo apt-get -y install autoconf intltool libgtk-3 libgspell-1 libgtksourceview-3.0-1 libwebkit2gtk-4.1-0 libgspell-1-2 libglib2.0-dev libdbus-glib2.0-cil
sudo apt-get -y install autoconf-archive gstreamer1.0-libav gstreamer1.0-plugins-good autoconf autotools-dev libgspell-1-dev libglib2.0-data gsettings-desktop-schemas-dev
sudo apt-get -y install libwebkit2gtk-4.0 libwebkit2gtk-4.0-dev gstreamer1.0-alsa gstreamer1.0-pulseaudio libgspell-1-2 clang libglib2.0-0 inxi
sudo apt-get -y install libgtksourceview-3.0-1 libgtksourceview-3.0-common libgtksourceview-3.0-dev libgl1-mesa-dri gspell-1-tests libglib2.0-bin libgtk-3-dev gettext
sudo apt-get -y install libgl1-mesa-dri gstreamer1.0-pulseaudio gstreamer1.0-libav gstreamer1.0-alsa intltool libgspell-1-common libglib2.0-cil-dev libxapp-gtk3-module
sudo apt-get -y install libwebkit2gtk-4.0 libwebkit2gtk-4.0-dev libxapp-gtk3-module gstreamer1.0-libav libgtk-3-dev libgspell-1-dev libglib2.0-cil
sudo apt-get -y install xapp-sn-watcher libxapp-gtk3-module libgspell-1-dev libgspell-1-dev auto-tools intltoolize libwebkit2gtk-4.1-dev

# Update package list again
sudo apt-get update

# YAD download
echo "Downloading YAD source code..."
wget https://github.com/v1cont/yad/releases/download/v14.1/yad-14.1.tar.xz

# Extract
echo "Extracting YAD source code..."
tar -xf yad-14.1.tar.xz

# Quick nap
sleep 10

# Change directory
echo "Changing directory to YAD source..."
cd yad-14.1

# It's strange but mandatory
echo "If this is not done yad will not work... YOU HAVE BEEN WARNED!!!!!!!!!"

# Confirm necessary packages are installed again
sudo apt-get -y install libwebkit2gtk-4.0-dev auto-tools intltoolize libgspell-1 libwebkit2gtk-4.0-dev libgtk-3-dev libglib2.0-0
sudo apt-get -y install automake build-essential intltool libglib2.0-dev libgtk-3-dev libglib2.0-dev libgtk-3-dev libglib2.0-dev-bin intltool
sudo apt-get -y install autoconf intltool libgtk-3 libgspell-1 libgtksourceview-3.0-1 libwebkit2gtk-4.1-0 libgspell-1-2 libglib2.0-dev libgtk-3-dev gettext
sudo apt-get -y install autoconf-archive gstreamer1.0-libav gstreamer1.0-plugins-good autoconf autotools-dev gspell-1-tests libglib2.0-bin libxapp-gtk3-module
sudo apt-get -y install libwebkit2gtk-4.0 libwebkit2gtk-4.0-dev gstreamer1.0-alsa gstreamer1.0-pulseaudio libgspell-1-common libglib2.0-cil-dev
sudo apt-get -y install libgtksourceview-3.0-1 libgtksourceview-3.0-common libgtksourceview-3.0-dev libgl1-mesa-dri gcc libglib2.0-data gsettings-desktop-schemas-dev
sudo apt-get -y install libgl1-mesa-dri gstreamer1.0-pulseaudio gstreamer1.0-libav gstreamer1.0-alsa intltool libwebkit2gtk-4.1-dev libdbus-glib2.0-cil
sudo apt-get -y install libwebkit2gtk-4.0 libwebkit2gtk-4.0-dev libxapp-gtk3-module gstreamer1.0-libav gir1.2-gspell-1 libglib2.0-cil inxi
sudo apt-get -y install xapp-sn-watcher libxapp-gtk3-module libgspell-1-dev libgspell-1-dev auto-tools intltoolize clang libdbus-glib2.0-cil-dev

echo "👉 The first part is done."

# Run autoreconf and intltoolize
autoreconf -ivf && intltoolize

echo "👉 The second part is done."

# Configure with options
./configure --enable-tools --enable-html --enable-sourceview --enable-webkit --enable-gtk --enable-spell --enable-tray --enable-tray --enable-deprecated --enable-icon-browser 

echo "👉 The third part is done."

# Build YAD
make
echo "Compilation complete."

echo "👉 The forth part is done."


# Install YAD
sudo make install

echo "👉 The fith part is done."

# Copy yad.m4 to the correct location
sudo cp yad.m4 /usr/share/aclocal

# Change to src directory
cd src

# Copy binaries to system paths
sudo cp yad /usr/bin/yad
sudo cp yad-tools /usr/bin/yad-tools
sudo cp yad-settings /usr/bin/yad-settings
sudo cp yad-icon-browser /usr/bin/yad-icon-browser

echo "👉 The user bin copying is done."

# Set permissions for binaries
sudo chmod a+x /usr/bin/yad
sudo chmod a+x /usr/bin/yad-tools
sudo chmod a+x /usr/bin/yad-settings
sudo chmod a+x /usr/bin/yad-icon-browser

echo "👉 The user bin permissions are set."

# Copy binaries to local bin
echo "Weird stuff again"
sudo cp yad /usr/local/bin/yad
sudo cp yad-tools /usr/local/bin/yad-tools
sudo cp yad-settings /usr/local/bin/yad-settings
sudo cp yad-icon-browser /usr/local/bin/yad-icon-browser

echo "👉 The user local bin copying is done."

# Set permissions for local binaries
sudo chmod a+x /usr/local/bin/yad
sudo chmod a+x /usr/local/bin/yad-settings
sudo chmod a+x /usr/local/bin/yad-icon-browser

echo "👉 The user local bin permissions are set."

# Return to home directory
cd ~

# Go to data directory
cd yad-dialog-code/data

# Copy desktop files
sudo cp yad-icon-browser.desktop /usr/share/applications
sudo cp yad-settings.desktop /usr/share/applications
sudo cp yad.gschemas.xml /usr/share/glib-2.0/schemas

echo "👉 The copying is done."



# Ensure the schemas directory exists and copy the gschema file
if [ ! -d "/usr/share/glib-2.0/schemas" ]; then
    echo "Creating directory /usr/share/glib-2.0/schemas as it does not exist."
    sudo mkdir -p /usr/share/glib-2.0/schemas
fi

# Copy icons to correct locations
cd icons
sudo cp 16x16/yad.png /usr/share/icons/hicolor/16x16/apps
sudo cp 24x24/yad.png /usr/share/icons/hicolor/24x24/apps
sudo cp 32x32/yad.png /usr/share/icons/hicolor/32x32/apps
sudo cp 96x96/yad.png /usr/share/icons/hicolor/96x96/apps
sudo cp 128x128/yad.png /usr/share/icons/hicolor/128x128/apps

echo "👉 The copying of icons is done."

# Set permissions for desktop files
sudo chmod 644 /usr/share/applications/yad-icon-browser.desktop
sudo chmod 644 /usr/share/applications/yad-settings.desktop
sudo chmod a+x /usr/share/glib-2.0/schemas/yad.gschema.xml

echo "👉 The permsioons are set."

# Update icon cache
gtk-update-icon-cache

# Refrsh
sudo apt-get update

# Cleanup
cd ..
rm yad-dialog-code

spinner $!

echo -e "\n[✔] YAD has installed successfully."
echo "👉 End Users feel free to modify this script to your likings."

# bye bye 
echo "   o/  "
echo "  /|   "
echo "  / \\  "
echo "Bye Bye!"
