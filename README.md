# AI HamScan

An at-home hamstring ultrasound: a wand with hand-cut piezoelectric transducers, plus two image models that grade a hamstring tear and identify which muscle it's in.

## Why I built it
I tore my hamstring playing hockey. Ultrasound is the first test for muscle injuries in Australia and Europe, but it isn't standard for this in the U.S. I wanted a way to check a hamstring injury at home.

## How it works
- **Wand:** 8 piezo transducers I cut and sanded by hand, scaled down from a 128-element commercial probe design.
- **Firmware (C, with DMA):** fires a 5 MHz pulse, then a transistor cuts the drive voltage so the same transducer can listen for the echo.
- **Imaging (Python):** combines 3 captures to raise signal-to-noise before building the image.
- **Two models in a row:** the first grades the tear (No lesion, Grade 1, Grade 2, Grade 3/4); the second identifies the muscle (BF, ST, SM).

## Try the models
- Tear grade model: [https://teachablemachine.withgoogle.com/models/RrrtHRP7_A/]
- Muscle model: [https://teachablemachine.withgoogle.com/models/dmXXlMcowL/]

## Data
No hamstring ultrasound database existed, so I built one. I cold-emailed 200+ radiologists and sports-medicine doctors (the best replies came from Australia and France) and pulled frames from teaching webinars, for 800+ images total. Two radiologists taught me to grade tears and checked my labels. 

## Files
- `models/grade/` and `models/muscle/`: the two exported Teachable Machine models
  
## Credit
- Both models were trained with Google's Teachable Machine. 
