This is a fork of the official [wasm3](https://github.com/wasm3/wasm3) interpreter modified to run on the original Xeon Phi. Since the Phi uses an old kernel of linux it lacks support for the getrandom() syscall. As such, I have reimplemented a simple (albeit not great) function to run in its place.

Compilation is simple, from source root simply run 
```bash
k1om-mpss-linux-gcc -O3 -g0 -s -Isource -Dd_m3HasWASI source/*.c platforms/app/main.c -lm -o wasm3
```

This will result in a wasm3 file being generated that can then be copied to the Xeon Phi via SCP.
