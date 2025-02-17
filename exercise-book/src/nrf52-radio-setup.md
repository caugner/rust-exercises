# Radio Setup

✅ Open the `nrf52-code/radio-app/src/bin/radio-send.rs` file.

✅ First run the program `radio-send.rs` as it is. You should see new output in the output of `cargo xtask serial-term`, if you left your Dongle on channel 20. If you change your Dongle's channel to avoid interference, change to the channel to match in `radio-send.rs` before you run it.

```console
$ cargo xtask serial-term
deviceid=588c06af0877c8f2 channel=20 TxPower=+8dBm app=loopback-fw
received 5 bytes (CRC=Ok(0xdad9), LQI=53)
```

The program broadcasts a radio packet that contains the 5-byte string `Hello` over channel 20 (which has a center frequency of 2450 MHz). The `loopback` program running on the Dongle is listening to all packets sent over channel 20; every time it receives a new packet it reports its length and the Link Quality Indicator (LQI) metric of the transmission over the USB/serial interface. As the name implies the LQI metric indicates how good the connection between the sender and the receiver is.

To repeatedly send a packet without re-flashing your DK, try pressing the BOOT/RESET button (next to the nRF USB connector that we aren't using yet).
