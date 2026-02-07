# Scriabin-Split
My first ergo split keyboard.
Alexander Nikolayevich Scriabin (Александр Николаевич Скрябин) is a pianist famous for his small hands. This project use his name as a reference of my basic requirement of my own keyboard.

## STILL IN PROGRESS!!!

## Warning
1. Current works are all working on [Official WebGUI](https://ergogen.ceoloide.com/). If you want to run locally, make sure you know how to configure footprints and the pcb block.
2. Can't define footprints for dynamical usage, even on [Ceoloide's WebGUI](https://ergogen.ceoloide.com/):
    - No errors and workable, but not dynamic and stupid:
        ```yaml
        meta:
            engine: 4.2.1
            # code ...
            switch_settings:
                # code ...
        units:
            $extends: meta.switch_settings.mx
        # code ...
        pcbs:
            left:
                template: kicad8
                outlines:
                main:
                    outline: plate_left
                footprints:
                mcu:
                    what: ceoloide/mcu_supermini_nrf52840 # <===== directly set here
                    where: 
                    ref: controller_left_board_r0 
                    params:
                    P1: C0
                    P0: C1
                    P2: C2
                    P3: C3
                    P4: C4
                    P5: C5
                    P6: C6
                    P7: C7
                    P21: R0
                    P20: R1
                    P19: R2
                    P18: R3
                    P15: R4
                    P14: R5
                choc_switches:
                    what: ceoloide/switch_mx # <===== directly set here
                    where: /^left.*/
                    params:
                    from: "{{column_net}}"
                    to: "{{row_net}}"
                diodes:
                    what: ceoloide/diode_tht_sod123 # <===== directly set here
                    where: /^left.*/
                    params:
                    from: "{{column_net}}"
                    to: "{{row_net}}"
                    adjust:
                    shift: [0, -5]
            right:
                # code ...
        ```
    - Error:
        ```yaml
        # presets
        meta:
            engine: 4.2.1
            # code ...
            footprint_settings: # define here is OK
                v1:
                mcu_footprint: ceoloide/mcu_supermini_nrf52840
                switch_footprint: ceoloide/switch_mx
                diode_footprint: ceoloide/diode_tht_sod123
            switch_settings:
                # code ...
        units:
            $extends: [meta.switch_settings.mx, meta.footprint_settings.v1] # but once footprint_settings got extended will get: "Error: Undefined symbol ceoloide"
        # code ...
        pcbs:
            left:
                template: kicad8
                outlines:
                main:
                    outline: plate_left
                footprints:
                mcu:
                    what: mcu_footprint # <===== I wanna write in this way
                    where: 
                    ref: controller_left_board_r0 
                    params:
                    P1: C0
                    P0: C1
                    P2: C2
                    P3: C3
                    P4: C4
                    P5: C5
                    P6: C6
                    P7: C7
                    P21: R0
                    P20: R1
                    P19: R2
                    P18: R3
                    P15: R4
                    P14: R5
                choc_switches:
                    what: switch_footprint # <===== I wanna write in this way
                    where: /^left.*/
                    params:
                    from: "{{column_net}}"
                    to: "{{row_net}}"
                diodes:
                    what: diode_footprint_ # <===== I wanna write in this way
                    where: /^left.*/
                    params:
                    from: "{{column_net}}"
                    to: "{{row_net}}"
                    adjust:
                    shift: [0, -5]
            right:
                # code ...
        ```

## Tools
- [Ergogen](https://github.com/ergogen/ergogen)
- [OpenSCAD](https://openscad.org/)
- [Kicad](https://www.kicad.org/)

## References
### Ergogen
- [Official documents](https://docs.ergogen.xyz/)
- [FlatFootFox's step-by-step tutorial](https://flatfootfox.com/ergogen-introduction/)
- [Ben Vallack's video tutorial](https://youtu.be/M_VuXVErD6E)
### QMK
- [ZiTe (SideraKB) - DIY a QMK Keyboard (Traditional Chinese)](https://blog.ziteh.dev/categories/%E8%87%AA%E8%A3%BDqmk%E9%8D%B5%E7%9B%A4)