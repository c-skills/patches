patches
=======

Inside this repo, you will find patches we made for some of our client projects which we were kindly allowed to publish here.

**Note: We might were only tasked to review certain corners of certain software and might not
shed light to the entire source or other parts that may or may not be interesting. As such, the proposed
patches may be incomplete, untested, broken or complete nonsense. If you happen to find working
patches, it does not endorse or promote the project as being clean or fully audited by us or others.***


Inside this repo you will find patches for:

* [tpm2-tss-engine](https://github.com/tpm2-software/tpm2-tss-engine)

The problem here is that the engine code trusts the TPM to only send valid data,
which might not be the case (think vTPMs or HW implants) when unmarshalling byte streams.
There are checks for internal buffer sizes during unmarshal, but these sizes not necessarily
match the target buffers the caller had in mind. The impact is not very high, but in
crypto you need to be picky. We also fixed a nice potential memory corruption when
decoding ECC compressed points inside `init_tpm_public_point()`.


