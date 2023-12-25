# Maintainer: bashonly <bashonly@protonmail.com>

pkgname=ffmpeg-bashonly
pkgver=6.1.bash1
pkgrel=4
pkgdesc='Complete solution to record, convert and stream audio and video'
arch=(x86_64)
url=https://ffmpeg.org/
license=(GPL3)
depends=(
  alsa-lib
  aom
  bzip2
  cairo
  fontconfig
  fribidi
  glib2
  glibc
  gmp
  gnutls
  gsm
  jack
  lame
  libass.so
  libavc1394
  libbluray.so
  libbs2b.so
  libdav1d.so
  libdrm
  libfreetype.so
  libgl
  libharfbuzz.so
  libiec61883
  libjxl.so
  libmodplug
  libopenmpt.so
  libplacebo.so
  libpulse
  librav1e.so
  libraw1394
  librsvg-2.so
  librubberband.so
  libsoxr
  libssh
  libtheora
  libva.so
  libva-drm.so
  libva-x11.so
  libvdpau
  libvidstab.so
  libvorbisenc.so
  libvorbis.so
  libvpx.so
  libwebp
  libx11
  libx264.so
  libx265.so
  libxcb
  libxext
  libxml2
  libxv
  libxvidcore.so
  libzimg.so
  ocl-icd
  onevpl
  opencore-amr
  openjpeg2
  opus
  sdl2
  snappy
  speex
  srt
  svt-av1
  v4l-utils
  vmaf
  vulkan-icd-loader
  xz
  zlib
)
makedepends=(
  amf-headers
  avisynthplus
  clang
  ffnvcodec-headers
  frei0r-plugins
  ladspa
  mesa
  nasm
  opencl-headers
  vulkan-headers
)
optdepends=(
  'avisynthplus: AviSynthPlus support'
  'frei0r-plugins: Frei0r video effects support'
  'intel-media-sdk: Intel QuickSync support (legacy)'
  'ladspa: LADSPA filters'
  'nvidia-utils: Nvidia NVDEC/NVENC support'
  'onevpl-intel-gpu: Intel QuickSync support'
)
provides=(
  ffmpeg
  libavcodec.so
  libavdevice.so
  libavfilter.so
  libavformat.so
  libavutil.so
  libpostproc.so
  libswresample.so
  libswscale.so
)
conflicts=(ffmpeg)
_backports=(
  'e9c93009fc34ca9dfcf0c6f2ed90ef1df298abf7' # Fix VDPAU vo
  'a562cfee2e214252f8b3f516527272ae32ef9532' # Fix bug in av_fft_end
  '250471ea1745fc703eb346a2a662304536a311b1' # Fix bug in av_fft_end
  '4cdf2c7f768015c74078544d153f243b6d9b9ac5' # Fix ftyp/invalid data received bug
)
source=(
  "https://ffmpeg.org/releases/ffmpeg-6.1.tar.gz"
  "https://ffmpeg.org/releases/ffmpeg-6.1.tar.gz.asc"
  "add-av_stream_get_first_dts-for-chromium.patch"
  "ffmpeg-${_backports[0]}.patch::https://git.ffmpeg.org/gitweb/ffmpeg.git/commitdiff_plain/${_backports[0]}"
  "ffmpeg-${_backports[1]}.patch::https://git.ffmpeg.org/gitweb/ffmpeg.git/commitdiff_plain/${_backports[1]}"
  "ffmpeg-${_backports[2]}.patch::https://git.ffmpeg.org/gitweb/ffmpeg.git/commitdiff_plain/${_backports[2]}"
  "ffmpeg-${_backports[3]}.patch::https://git.ffmpeg.org/gitweb/ffmpeg.git/commitdiff_plain/${_backports[3]}"
)
# Import key with: curl https://ffmpeg.org/ffmpeg-devel.asc | gpg --import
validpgpkeys=('FCF986EA15E6E293A5644F10B4322F04D67658D8')  # FFmpeg release signing key <ffmpeg-devel@ffmpeg.org>
sha256sums=(
  '938dd778baa04d353163ca5cb06c909c918850055f549205b29b1224e45a5316'
  'a88e632545ff91ad6b80642f9c443fd7d23f1d9413188a084fd4a06a714fc8dc'
  '57e26caced5a1382cb639235f9555fc50e45e7bf8333f7c9ae3d49b3241d3f77'
  # backport commit patches
  '082b4d383528c22ab9791e32234f80fb66d7378e02fa043f9640ee2deac28f91'
  '490957bf0a24db91a6391b4b45b5d49fbf9af0a757b0f3b5e961401c5ce406ae'
  '8fef9dc1f3f141ef069a3a2a0fbe87e653f844e6b99dcc1d6fdab4cf7458541f'
  '99d3960f7bdf472f85a7508428153bc52d10f39aab3e36d782f00adf3eeeed39'
)

prepare() {
  cd ffmpeg-6.1
  # https://crbug.com/1251779
  patch -Np1 -i ../add-av_stream_get_first_dts-for-chromium.patch
  local _backport
  for _backport in "${_backports[@]}"; do patch -p1 -i "../ffmpeg-${_backport}.patch"; done
}

build() {
  cd ffmpeg-6.1
  ./configure \
    --prefix=/usr \
    --disable-debug \
    --disable-static \
    --disable-stripping \
    --enable-amf \
    --enable-avisynth \
    --enable-cuda-llvm \
    --enable-lto \
    --enable-fontconfig \
    --enable-frei0r \
    --enable-gmp \
    --enable-gnutls \
    --enable-gpl \
    --enable-ladspa \
    --enable-libaom \
    --enable-libass \
    --enable-libbluray \
    --enable-libbs2b \
    --enable-libdav1d \
    --enable-libdrm \
    --enable-libfreetype \
    --enable-libfribidi \
    --enable-libgsm \
    --enable-libharfbuzz \
    --enable-libiec61883 \
    --enable-libjack \
    --enable-libjxl \
    --enable-libmodplug \
    --enable-libmp3lame \
    --enable-libopencore_amrnb \
    --enable-libopencore_amrwb \
    --enable-libopenjpeg \
    --enable-libopenmpt \
    --enable-libopus \
    --enable-libplacebo \
    --enable-libpulse \
    --enable-librav1e \
    --enable-librsvg \
    --enable-librubberband \
    --enable-libsnappy \
    --enable-libsoxr \
    --enable-libspeex \
    --enable-libsrt \
    --enable-libssh \
    --enable-libsvtav1 \
    --enable-libtheora \
    --enable-libv4l2 \
    --enable-libvidstab \
    --enable-libvmaf \
    --enable-libvorbis \
    --enable-libvpl \
    --enable-libvpx \
    --enable-libwebp \
    --enable-libx264 \
    --enable-libx265 \
    --enable-libxcb \
    --enable-libxml2 \
    --enable-libxvid \
    --enable-libzimg \
    --enable-nvdec \
    --enable-nvenc \
    --enable-opencl \
    --enable-opengl \
    --enable-shared \
    --enable-version3 \
    --enable-vulkan
  make
  make tools/qt-faststart
  make doc/ff{mpeg,play}.1
}

package() {
  make DESTDIR="${pkgdir}" -C ffmpeg-6.1 install install-man
  install -Dm 755 ffmpeg-6.1/tools/qt-faststart "${pkgdir}"/usr/bin/
}
