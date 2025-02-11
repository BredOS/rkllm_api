# Maintainer: Bill Sideris <bill88t@bredos.org>

pkgname=rkllm_api
pkgver=r147.29fbc9b
pkgrel=1
arch=('aarch64')
pkgdesc="RKNN LLM API runtime"
url="https://github.com/Pelochus/ezrknn-llm/"
license=('custom')
source=(git+https://github.com/Pelochus/ezrknn-llm)
sha256sums=('SKIP')

pkgver() {
    cd "$srcdir/ezrknn-llm"
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
    cd "$srcdir/ezrknn-llm/rkllm-runtime/runtime/Linux/librkllm_api/include"

    # Patch rkllm.h to include cstdint
    echo '#include <cstdint>' | cat - "rkllm.h" > temp && mv temp "rkllm.h"
}

package() {
    cd "$srcdir/ezrknn-llm"
    mkdir -p "$pkgdir/usr/lib/" "$pkgdir/usr/local/include"
    install -Dm644 rkllm-runtime/runtime/Linux/librkllm_api/aarch64/* "$pkgdir/usr/lib/"
    install -Dm644 rkllm-runtime/runtime/Linux/librkllm_api/include/* "$pkgdir/usr/local/include/"
}
