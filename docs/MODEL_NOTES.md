# Model Notes

The repository model is based on the supplied Simulink file. Its initialization configuration contains:

- fsw = 10e3
- fref = 50
- Vodref = 220*sqrt(2)
- Voqref = 0
- Vdc = 700
- Lf = 3.5e-3
- Rf = 0.1
- Cf = 50e-6
- Lc = 0.35e-3
- Rc = 0.05
- mp = 5e-5
- np = 3e-3

Controller gains are calculated from these parameters and derived control-bandwidth relationships inside the model initialization.
