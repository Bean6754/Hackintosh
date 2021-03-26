This is the guide that I followed: (https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html)

# BIOS

I had to disable these in order to get the installer working:
- CFG-Lock.
- Intel VT-d.
- Parallel and Serial.
- XHCI Hand-off.

After installation I was able to re-enable `Intel VT-d` and `XHCI Hand-off`.

# config.plist

You need to replace the UUID, ROM and serial-number in `config.plist`.

You can generate these by:

- Source: (https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#using-gensmbios)

## UUID:

Type uuidgen in Terminal

`$ uuidgen`

976AA603-75FC-456B-BC6D-9011BFB4968E

## Serial number:

```
git clone --depth 1 https://github.com/acidanthera/OpenCorePkg.git
cd ./OpenCorePkg/Utilities/macserial/
make
chmod +x ./macserial
```

Find your SystemProductName in your config.plist file. That is your model number.

Replace "iMac19,1" below with SystemProductName in your `config.plist`.

`./macserial --num 1 --model "iMac19,1"`
