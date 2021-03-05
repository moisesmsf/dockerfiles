FROM debian:buster-slim

ARG LANG=${LANG}

ENV HOME=/home/r

ENV USER=r

ENV UID=1000

ENV LANG=${LANG}

ENV FIREFOX_DEPS \
adwaita-icon-theme dbus dbus-user-session dconf-gsettings-backend \
  dconf-service dmsetup fontconfig fontconfig-config fonts-dejavu-core \
  glib-networking glib-networking-common glib-networking-services \
  gsettings-desktop-schemas gtk-update-icon-cache hicolor-icon-theme \
  libapparmor1 libargon2-1 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data \
  libatspi2.0-0 libavahi-client3 libavahi-common-data libavahi-common3 libbsd0 \
  libcairo-gobject2 libcairo2 libcap2 libcolord2 libcroco3 libcryptsetup12 \
  libcups2 libdatrie1 libdbus-1-3 libdbus-glib-1-2 libdconf1 \
  libdevmapper1.02.1 libepoxy0 libevent-2.1-6 libexpat1 libfontconfig1 \
  libfreetype6 libfribidi0 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common \
  libglib2.0-0 libgraphite2-3 libgssapi-krb5-2 libgtk-3-0 libgtk-3-common \
  libharfbuzz0b libicu63 libidn11 libip4tc0 libjbig0 libjpeg62-turbo \
  libjson-c3 libjson-glib-1.0-0 libjson-glib-1.0-common libk5crypto3 \
  libkeyutils1 libkmod2 libkrb5-3 libkrb5support0 liblcms2-2 libncurses6 \
  libpam-systemd libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 \
  libpixman-1-0 libpng16-16 libprocps7 libproxy1v5 libpsl5 librest-0.7-0 \
  librsvg2-2 librsvg2-common libsoup-gnome2.4-1 libsoup2.4-1 libsqlite3-0 \
  libssl1.1 libthai-data libthai0 libtiff5 libwayland-client0 \
  libwayland-cursor0 libwayland-egl1 libwebp6 libx11-6 libx11-data libx11-xcb1 \
  libxau6 libxcb-render0 libxcb-shm0 libxcb1 libxcomposite1 libxcursor1 \
  libxdamage1 libxdmcp6 libxext6 libxfixes3 libxi6 libxinerama1 libxkbcommon0 \
  libxml2 libxrandr2 libxrender1 libxt6 lsb-base procps sensible-utils \
  shared-mime-info systemd systemd-sysv ucf xkb-data

COPY entrypoint.sh /usr/bin/entrypoint.sh

RUN useradd -m $USER \
    && apt update &&  apt install -y --no-install-recommends curl tar bzip2 apulse $FIREFOX_DEPS \
    && curl --insecure --location "https://download.mozilla.org/?product=firefox-latest-ssl&os=linux64&lang=en-US" --output $HOME/firefox.tar.bz2 \
    && tar -xvjf $HOME/firefox.tar.bz2 -C $HOME && rm $HOME/firefox.tar.bz2 \
    && ln -sf $HOME/firefox/firefox /usr/local/bin/firefox && chmod +x /usr/bin/entrypoint.sh /usr/local/bin/firefox

USER $USER

ENTRYPOINT [ "entrypoint.sh" ]
