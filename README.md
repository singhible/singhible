<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&height=180&color=gradient" />

<p align="center">
  <img src="https://raw.githubusercontent.com/singhible/singhible/main/anim/name.svg" width="600" alt="Baban" />
</p>

<p align="center">Software engineer</p>

---

I like understanding how things work all the way down. I have a soft spot for software that works on your own machine without phoning home, which is probably why I keep ending up in kernel and embedded Linux. 

**Stack:** C · Python · Kernel · Yocto & embedded Linux

## Upstream work

I send patches to the Linux kernel and to OpenEmbedded-Core, the base layer of the Yocto Project. So far that's 19 commits in mainline Linux and 8 in OE-Core, where I also maintain the libusb1 and stress-ng recipes.

The ones I'd point you at:

- [w1: ds2482: Fix signedness bug in ds2482_w1_triplet()](https://git.kernel.org/torvalds/c/4d3721b204f9). An I2C error in the middle of a 1-Wire ROM search got truncated into a believable search result. The search kept going on a made-up bit and could miss a real device or register one that doesn't exist.
- [power: supply: sbs-battery: Use a per-device serial number buffer](https://git.kernel.org/torvalds/c/6027892925b8). Every battery on the system formatted its serial number into one shared buffer, so reading two batteries at once could give you the wrong battery's serial.
- [counter: microchip-tcb-capture: Fix DT channel validation](https://git.kernel.org/torvalds/c/f1a3a9946aab). A u32 read into an int let a malformed devicetree slip a negative channel past the bounds check and into register offset math.
- [pid: use READ_ONCE() in pid_alive()](https://git.kernel.org/torvalds/c/12e19bba68ba4). Data race on `task->thread_pid` that syzbot caught with KCSAN.
- [devtool: standard: fix update-recipe/finish --initial-rev override](https://git.openembedded.org/openembedded-core/commit/?id=62abb60b899e63ea6db5c745f4b1b6af0d4b40f1). Passing `--initial-rev` failed with the error message telling you to pass `--initial-rev`. It had been broken since submodule support went in.
- [devtool: standard: fix finish/update-recipe for recipes using AUTOREV](https://git.openembedded.org/openembedded-core/commit/?id=ae7be93cfd63088f6f160e75a99d9eaca1e1bd7f). Crashed because SRCREV expands to the literal placeholder `AUTOINC`, which git doesn't know what to do with.

The full lists, which stay current on their own:

- [My commits in Linux](https://github.com/search?q=repo%3Atorvalds%2Flinux+author%3Asinghible&type=commits)
- [My commits in OE-Core](https://github.com/openembedded/openembedded-core/commits?author=singhible)
- [My patches on lore.kernel.org](https://lore.kernel.org/all/?q=f%3A%22Babanpreet+Singh%22), including ones still in review
