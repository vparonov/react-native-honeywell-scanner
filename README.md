# react-native-honeywell-scanner

This module is fork of react-native-honeywell-scanner.

## Getting started

`$ npm install react-native-honeywell-scanner --save`

## Usage
```javascript
import HoneywellScanner from 'react-native-honeywell-scanner';

...

useEffect(() => {
        if( HoneywellScanner.isCompatible ) {
            HoneywellScanner.startReader().then((claimed) => {
                console.log(claimed ? 'Barcode reader is claimed' : 'Barcode reader is busy');
                HoneywellScanner.onBarcodeReadSuccess(event => {
                    console.log('Received data', event.data);
                });

            });


            return(
                () => {
                    HoneywellScanner.stopReader().then(() => {
                        console.log("Freedom!!");
                        HoneywellScanner.offBarcodeReadSuccess();
                    });
                }
            )
        }
    }, []);
```