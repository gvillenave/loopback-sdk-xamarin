# README #

### What is this repository for? ###

Creation of Loopback SDK for Xamarin Studio or C# project.

* Quick summary: 
    The Repository contains 3 folders.
    "lb-xm" folder contains the SDK Generator: JS Code running a compiled c# code that creates the SDK. E.g. In shell "node lb-xm d:\someserver\server\server.js" will create CS code for the SDK, whereas "node lb-xm d:\someserver\server\server.js c sdk.dll" will compile an sdk DLL. 
    Second folder, "LBXamarinSDK", contains the open source of the c# part of the generator. 
    Thirdly, "SDK Example" folder contains the example server and Xamarin solution of an App using a compiled SDK.

* Version 1.0

### How do I get set up? ###

* On Windows
	1. Go into lb-xm and run 'npm install' in shell.
* On MacOS
	1. Have Homebrew installed - 'ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"'.
	2. If you don't have Mono x64 installed, run 'brew install https://raw.githubusercontent.com/tjanczuk/edge/master/tools/mono64.rb' in shell.
	3. run 'brew install pkg-config'.
	4. run 'npm install'.
* After Setup

    To compile an SDK, take the folder "lb-xm", make sure you have all the dependencies and run "node lb-xm d:\someserver\server\server.js c sdk.dll" in shell, where first parameter is the server.js file of the Loopback server, c is a compilation flag and sdk.dll is the filename of the output compiled SDK.
    To review the C# part of the Generator (Source code of lb-xm/bin/LBXamarinSDKGenerator.dll), take the folder "LBXamarinSDK" and "LBXamarinSDK.sln" which is a Visual Studio solution.
    To review the example App using a compiled SDK, take the folder "SDK Example". This folder in turn contains a Loopback server and a Xamarin solution of an Android App using the SDK.






### Testers for LBXamarinSDK ###

* A tester pack for the LBXamarinSDK
* Version 1.0.0

### Basic info ###
=========
Contents:
=========
relationsServer - a basic server to test on

UnitTests - Xamarin solution with testers for the relationsServer

================
About the tests:
================
There are three sections of testing:
1. CRUD tests for all models except for miniUser (which is the user model):
2. CRUD tests for the miniUser model
3. Relation tests between Customer and Orders + Reviews

The CRUD tests assume predefined data on the server
Relation Tests are pseudo - dynamic


### Setup ###
1. go to relationsserver directory
2. do 'npm install' to install server

### Runnig tests ###
1. 'slc run' in the relationsServer directory (Tesminal/cmd)
2. run the UnitTests.sln from UnitTests dir
3. Run tests

Warning!!!
each time you run a test, there should be a restart of the server, 
otherwise CRUD test will fail, because values are changed during the tests.

=====================================
Instructions for the relations Tests:
=====================================
The tester creates 3 customers.
The user can change the code in order to controll the amount on orders/reviews

=======================================================================
Changing the [Testfixture(new int[] { 3, 3, 3 },new int[] { 3, 3, 3 })]
=======================================================================

array1 - orders.
===============
array1[0] - contains the number of orders for customer 1.
etc.

array2 - reviews.
===============
array1=2[0] - contains the number of reviews for customer 1.
etc.

Minimum Values - minimum values should be >= 3, otherwise tests will fail!
