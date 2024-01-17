##Licensing
How do we handle things like torchvision and huggingface WRT legal. Especially around downloaded weights. Is there a significant difference between including weights, automatically downloading weights and having to download weights by hand?

This will end up effecting llama-cpp, torchvision, huggingface, stable-diffusion.cpp and potentially others but llama-cpp and stable-diffusion.cpp are the least likely to be affected due to their requirements for downloading weights by hand.

Conclusion: leave questionable bits out of packages for now, tflink to start conversation with legal on what we’re allowed to include in the packages.

##Package Reviews
Still waiting on a few reviews, should be blocking the [ML SIG review tracker](https://bugzilla.redhat.com/show_bug.cgi?id=1011110)

Getting close to enabling rocm based accelleration in pytorch but that’s still blocked on a few reviews (at least rocfft, hipfft once rocfft is reviewed).
