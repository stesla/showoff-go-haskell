!SLIDE center
# Monads

!SLIDE bullets incremental
# WTF Are Monads?
* Concept from Category Theory
* Types that represent computation
* A means to remove boiler-plate
* A means to provide side-effects

!SLIDE
# A brief digression...

!SLIDE
# The Maybe type
    data Maybe a = Just a | Nothing

# Great for things like association lookups
    > let alist = [(1,2), (3,4)]
    > lookup 1 alist
    Just 2
    > lookup 42 alist
    Nothing

!SLIDE code
    chainLookup key1 alist1 alist2 alist3 =
       case lookup key1 alist1 of
          Nothing -> Nothing
          | key2 ->
              case lookup key2 alist2 of
                 Nothing -> Nothing
                 | key3 ->
                    lookup key3 alist3

!SLIDE
# OMG that is ugly!

!SLIDE code smaller
# Imagine a function:
    (>>=) :: Maybe a -> (a -> Maybe b) -> Maybe b
    Nothing >>= _ = Nothing
    Just x  >>= f = f x

!SLIDE code
    chainLookup key1 alist1 alist2 alist3 =
       lookup key1 alist1 >>=
       \key2 -> lookup key2 alist2 >>=
       \key3 -> lookup key3 alist3

!SLIDE
# That's still a bit noisy

!SLIDE code
    chainLookup key1 alist1 alist2 alist3 = do
      key2 <- lookup key1 alist1
      key3 <- lookup key2 alist2
      lookup key3 alist3

!SLIDE
# Anyway. Back to Monads.

!SLIDE code
# The Monad Typeclass
    class Monad m where
      (>>=) :: m a -> (a -> m b) -> m b
      (>>) :: m a -> m b -> m b
      return :: a -> m a
      fail :: String -> m a

!SLIDE bullets incremental
# Interesting Monads
* Maybe
* IO
* State
* STM
