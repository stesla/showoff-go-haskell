!SLIDE center
# Types

!SLIDE bullets incremental
# What are types?
* Descriptors
* Data
* Storage
* Behavior

!SLIDE
## Types help us make safe programs.

!SLIDE bullets incremental
# Haskell's Types Are
* Statically checked
* Inferenced
* Polymorphic
* Abstract

!SLIDE code
# Some types
    42 :: Int

    4.2 :: Float

    "foo" :: String

    [True, False] :: [Bool]

    (4, "foo") :: (Int, String) 

!SLIDE code
# Function types
     add :: Int -> Int -> Int

     add 5 :: Int -> Int

     (<) :: Int -> Int -> Bool

!SLIDE
# Typeclasses
## Define groups of functions as a type
    @@@
    class Eq a where
      (==) :: a -> a -> Bool
      (/=) :: a -> a -> Bool

## Use those typeclasses in signatures
    @@@
    myFunc :: (Eq a) => a -> a -> Bool

!SLIDE
# Typeclasses Help Design
## They show you what functions belong together.
    @@@
    class Num a where
      (+) :: a -> a -> a
      (*) :: a -> a -> a
      (-) :: a -> a -> a
      negate :: a -> a
      abs :: a -> a
      fromInteger :: Integer -> a

!SLIDE center
## Programming with a good type system is almost like programming with a pair.

!SLIDE center
# [Example: Money](http://gist.github.com/273293)
# [Example: S-Expressions](http://gist.github.com/273355)