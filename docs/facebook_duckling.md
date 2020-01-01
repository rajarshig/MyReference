# Facebook Duckling
[https://github.com/facebook/duckling](https://github.com/facebook/duckling)

Duckling is a Haskell library that parses text into structured data.
```
"the first Tuesday of October"
=> {"value":"2017-10-03T00:00:00.000-07:00","grain":"day"}
```

## Install Haskell stack
- Official documentation
[https://haskell-lang.org/get-started/linux](https://haskell-lang.org/get-started/linux)
- In Ubuntu
```
wget -qO- https://get.haskellstack.org/ | sh
```
- Quickly run a haskell script. Copy the following content into a file called HelloWorld.hs
```
#!/usr/bin/env stack
-- stack --install-ghc runghc

main :: IO ()
main = putStrLn "Hello World"
```

- Open up a terminal and run stack HelloWorld.hs.
- Start on a proper Haskell package. Run the following in your terminal:
```
stack new new-project
cd new-project
stack build
stack exec new-project-exe
```
- You can now edit the source files in this directory (see the file src/Lib.hs), and rebuild and run the project with stack build and stack exec new-project-exe as above.

## Install duckling
- Install PCRE
```
apt-get install libpcre3 libpcre3-dev
```
- Clone and cd to folder
```
https://github.com/facebook/duckling.git
cd duckling
```
- Compile and build
```
stack build
stack exec duckling-example-exe
```
- The first time you run it, it will download all required packages.This runs a basic HTTP server. Example request:
```
curl -XPOST http://0.0.0.0:8000/parse --data 'locale=en_GB&text=tomorrow at eight'
```

## Explore corpus data to understand the capabilities of the library
[https://github.com/facebook/duckling/blob/master/Duckling/Time/EN/Corpus.hs](https://github.com/facebook/duckling/blob/master/Duckling/Time/EN/Corpus.hs)

## Limit CPU usage by duckling server
-  Configure the Haskell runtime system using (to use 4 OS threads)
[https://github.com/facebook/duckling/issues/193](https://github.com/facebook/duckling/issues/193)
```
stack exec -- duckling-example-exe +RTS -N4 -RTS
```
