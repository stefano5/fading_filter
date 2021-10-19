# fading_filter

This is a recursive filter, based on sequential measurement data, giving more (or less) value to new measurement respect the old values. (fading old values...)

The filter is a linear combination of the old estimate and a heuristic gain that multiplies the residual.

In this way is it possible to estimate a signal and its first and second derivative.

This filter required just one parameter, let's call it "beta".


## First order filter

The equation is:

![Screenshot_20211019_230810](https://user-images.githubusercontent.com/40228829/137990786-1590d8d6-cd19-4ce6-b08b-b3d66c54202e.png)


Here is clear how beta act. Beta is supposed to be 0 < beta < 1.
* beta close to 0: you don't trust the measurements, the filter is very slow (expect delay) but the estimated value will be less noise
* beta close to 1: you trust a lot the measurements, the filter is very fast but the estimated value will be noise


Example, suppose we have a real signal whose behavior is sinusoidal. Suppose it is affected by white noise. 
Suppose also a Ts=1/100 (sampling time = 100Hz). Please set the Ts by the matlab command windows. 

Let beta=0.2, the estimated signal will be:

![beta02](https://user-images.githubusercontent.com/40228829/137989111-48690935-7fe0-42df-8ed3-a42c6fbb08a8.jpg)

There is a lot of noise!

Let beta=0.8:

![beta08](https://user-images.githubusercontent.com/40228829/137989539-e10d2f1c-7b28-4493-a554-ae6ae9bb04e1.jpg)

Now there is less noise, let's see if we put beta=0.98:

![beta098](https://user-images.githubusercontent.com/40228829/137989851-0fb31d95-fba4-489e-bc06-02723b8a14c6.jpg)

the noise has almost disappeared, but now there is a large delay!

Then for a signal with this noise we need 0.8 < beta < 0.98.

Beta is a trial and error parameter, it needs a trade off procedure.

There are also the implementation for a second and third order filter, the equations are quite different (but don't care) but the use is exactly the same!

In fact:

![Screenshot_20211019_231458](https://user-images.githubusercontent.com/40228829/137991654-8c43310a-1175-46bf-83b9-61f5337cc1c1.png)





