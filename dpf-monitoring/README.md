# DPF Monitoring for iDrive 8

> **iDrive 8 version (`dpf_id8` 0.1.0).** This is DPF Monitoring from [mgu-apps](https://github.com/giuseppesalatino-boop/mgu-apps) (DPF Monitoring 0.1.1), with its screens laid out for iDrive 8: the kit's iDrive 8 screens, drawn by the MGU Store's renderer (mgu-render) across a page about 2200 x 520 wide instead of 1600 x 520. Overview's bars, Live data's histories and list, and History's two halves take the extra width; the kit's header shows the pages as tabs. What it measures, reads and saves is unchanged, and the rest of this README describes it as it is on iDrive 7. **It hasn't run on an iDrive 8 car yet** and isn't in the MGU Store: see the [collection's README](../README.md#what-still-needs-a-car).

The diesel particulate filter of a BMW diesel on the iDrive 7 (MGU) head unit, in the look of BMW's own screens: soot and ash load, regenerations (live, interrupted, history), differential pressure and exhaust temperatures, read from the diesel engine unit (DDE) with UDS `0x22` ReadDataByIdentifier only. Nothing is ever written to the car.

- **Overview:** soot load and exhaust temperature as bars, a drawing of the filter with soot, ash, heat and the pressure difference, and the status (filter OK / regeneration due / running).
- **Live data:** soot, pressure difference and both exhaust temperatures with their last 5 minutes; every other value as a list, with the raw replies on request.
- **History:** the regenerations the app has watched and the intervals from the engine unit's memory.

The identifiers are in `app/app.json` (`config.dpf`), from the public SGBD reference of the G-series DDE 8.3 (B37 / B47 / B57).

## Install

Not in the MGU Store yet. To try it on an iDrive 8 car, see [Trying one on a car](../README.md#trying-one-on-a-car) in the collection's README. From a PC, with an oap-sdk from an iDrive 8 head unit in the collection's `vendor/idrive7-apps/oap-sdk/`: `npm run build:car`, then install `vendor/idrive7-apps/dist/dpf_id8@<version>.tgz` with the Store's deploy tool. It contains BMW's SDK: for your own car only, never publish it.

## Emulator

From this folder: `npm run emu` (an iDrive 8 screen; `npm run emu -- --id7` for iDrive 7's), then open http://localhost:8077. Without a DDE to answer, the app shows its demo values.

## Disclaimer

- **Not affiliated with BMW.** This is an independent, non-commercial project. It is not made, endorsed, supported or approved by BMW AG or any of its companies. BMW, iDrive and the names of BMW's models and control units are trademarks of BMW AG, used here only to say which cars and head units the software is for. No BMW logo, BMW software, BMW SDK or BMW data is part of this repository.
- **Read-only.** The apps only read values the car already provides; they never write to, code or flash a control unit, and they do not unlock or bypass any paid or protected function of the car.
- **At your own risk.** The software is provided "as is", without warranty of any kind (see LICENSE). Installing custom apps needs a modified head unit, which may affect the vehicle's warranty, and the values shown are estimates from the car's sensors. Use it only where it is legal and safe: performance runs only on closed courses, never on public roads, and don't operate the screen while driving.

## Licence

MIT ([LICENSE](LICENSE)). Built on [idrive7-apps](https://github.com/cauliflowermossgrape/idrive7-apps) by cauliflowermossgrape (MIT), from its DPF Monitor. Not affiliated with or endorsed by BMW.
