For anyone who wants to experiment with a newer Buildroot2 version or Linux
kernel version:
  - Buildroot2 target version is determined by images/conf
    Any changes to the Buildroot2 target version may require a new buildroot
    .config file to be created.  The actual files from the source tarball are
    kept in images/buildroot/{32,64}bit/.config but making changes to them
    should properly be done by:
         execute "./buildpbaroot" the normal way from the images directory
	 cd scratch/buildroot/32bit
	 make menuconfig
	   [Make any changes as needed]
         cd ../64bit
 	 make menuconfig
	   [Again, make any changes as needed]
         cd ..
         make O=32bit
         make O=64bit
	   [Now do whatever testing you believe is needed for the resulting
            output]
	   [Once you're happy, make sure you save those new 32bit/.config
	    and 64bit/.config files somewhere, so you can use them again
	    in the future.]
  - Linux kernel version is determined by a config line in the buildroot
    .config files above; however updating to a newer Linux kernel may
    require new kernel.config files.  Changes of that sort can be 
    accomplished similar to what's shown above:
	 execute "./buildpbaroot" the normal way from the images directory
	 cd scratch/buildroot/32bit/build/linux-4.14.213
	 make menuconfig
	   [Make any changes as needed]
         cd ../../../64bit/build/linux-4.14.213
 	 make menuconfig
	   [Again, make any changes as needed]
         cd ../../..
         make O=32bit
         make O=64bit
	   [Now do whatever testing you believe is needed for the resulting
            output kernels]
	   [Once you're happy, make sure you save those new .config files
	    for 32bit and 64bit kernels somewhere as 32bit/kernel.config
	    and 64bit/kernel.config, so you can use them again
	    in the future.]

