This is a small python script, which makes extensive use of boto, to provide human-readable out similar to ec2-describe-instances (ec2din). fec2din can be run with no arguments or a single argument of a specific instance ID. Simply named "f" + "ec2din", the command can easily be run after viewing the horrific ec2din output by simply typing "f!!" in a modern shell. This simple shortcut is why I left the standard ".py" extension off.

This script requires boto to be installed

$ easy_install boto

or

$ pip install boto

Example
=======
```
$ ec2din
RESERVATION	r-57192e11	103757199432	production
INSTANCE	i-89ba1299	ami-a7f539ce	ec2-50-99-41-60.compute-1.amazonaws.com	ip-10-99-241-197.ec2.internal	running	production	0		t1.micro	2011-11-09T07:16:45+0000	us-east-1c	aki-805ea7e9			monitoring-disabled	50.99.41.60	10.99.241.197			ebs					paravirtual	xen	sg-c129fe91	default
BLOCKDEVICE	/dev/sda1	vol-938be057	2011-11-09T07:17:07.000Z	
BLOCKDEVICE	/dev/sdj	vol-c47fb1a9	2011-11-09T07:36:06.000Z	
BLOCKDEVICE	/dev/sdk	vol-604da915	2011-11-09T17:18:37.000Z	

$ f!!
fec2din
= i-f1d4da85 =
AMI:	ami-37493714
Type:	m2.2xlarge (x86_64)
Public:	122.91.39.189 (ec2-122-91-39-189.compute-1.amazonaws.com)
PrivIP:	10.92.16.121
PubKey:	my-pub-key
Days:	9 (2012-06-15)
AZ:	us-east-1b
Group:	my-security-group, web-server, memcache
	ROOT  ( ephemeral )
	/dev/sdl
	/dev/sdk
```

Installation
=================================
Put fec2din in your path, chmod +x. Ensure boto is installed and your access & secret key are exported as environment variables:
```
 export EC2_ACCESS_KEY=JFIOQNAKEIFJJAKDLIJA
 export EC2_SECRET_KEY=3jfioajkle+OnfAEV5OIvj5nLnRy2jfklZRop3nn
```

If you are not using the us-east-1 region, you can set alternate endpoints in two ways:
```
 export EC2_REGION=us-west-1
```
or
```
 export EC2_URL=https://ec2.ap-southeast-1.amazonaws.com
```

Theoretically, you could set the EC2_URL endpoint to any EC2 compatible endpoint, such as Eucalyptus, using:
```
 export EC2_URL=https://localhost/services/Eucalyptus
```
but I have not tried it yet.

These variables could also be set at the top of the script if you want to hard-code them, but you'll have to reset them everytime you upgrade. I recommend putting them in your ~/.bashrc or wherever your shell wants them.
