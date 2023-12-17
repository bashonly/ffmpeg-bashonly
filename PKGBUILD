# Maintainer: bashonly <bashonly@protonmail.com>

pkgname=ffmpeg-bashonly
pkgver=6.1.bash1
pkgrel=3
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
options=(
  debug
)
source=(
  'ffmpeg-6.1.tar.gz::https://ffmpeg.org/releases/ffmpeg-6.1.tar.gz'
  '01-add-av_stream_get_first_dts-for-chromium.patch'
  '02-e9c93009fc34ca9dfcf0c6f2ed90ef1df298abf7.patch'
  '03-a562cfee2e214252f8b3f516527272ae32ef9532.patch'
  '04-250471ea1745fc703eb346a2a662304536a311b1.patch'
  '05-4cdf2c7f768015c74078544d153f243b6d9b9ac5.patch'
)
sha256sums=(
  '938dd778baa04d353163ca5cb06c909c918850055f549205b29b1224e45a5316'
  '57e26caced5a1382cb639235f9555fc50e45e7bf8333f7c9ae3d49b3241d3f77'
  '305ce9c2a1d42e6a83f333aed0357cacf3bf0029b047559315e5da56903a5296'
  '0f7403c3f57f7229f17d00ad1433e0314c55c57eecc63d4d7aec03fbdfd4c9cf'
  '47b5d5046d345a785747d76cf6f81b2809073e287d6a40f90bcecf4671aef34d'
  '82dc141f367888e0f12ca3c970bba9319a0599e1f767cc5a61acac753508fe19'
)

prepare() {
  cd ffmpeg-6.1
  # https://crbug.com/1251779
  patch -Np1 -i ../01-add-av_stream_get_first_dts-for-chromium.patch
  # Fix VDPAU vo
  patch -p1 -i ../02-e9c93009fc34ca9dfcf0c6f2ed90ef1df298abf7.patch
  # Fix bug in av_fft_end
  patch -p1 -i ../03-a562cfee2e214252f8b3f516527272ae32ef9532.patch
  patch -p1 -i ../04-250471ea1745fc703eb346a2a662304536a311b1.patch
  # Fix ftyp/invalid data bug
  patch -p1 -i ../05-4cdf2c7f768015c74078544d153f243b6d9b9ac5.patch
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
