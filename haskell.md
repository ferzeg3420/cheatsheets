---
title: Haskell
---

# Haskell

```
-- This is a single-line comment and the name of the interpreter is GHCI

{- Multiline
   Comments
-} 
```

## Misc prelude functions

```
succ :: Enum a => a -> a
succ x                      
```

The succ function returns x + 1

```
min :: Ord a => a -> a -> a
min x y
```

The min function returns the minimum of two things

```
max :: Ord a => a -> a -> a
max x y                           
```

The max function returns the maximum of two things

```
odd :: Integral a => a -> Bool
odd n                             
```

The odd function returns true if the integer is odd

```
even :: Integral a => a -> Bool
even n                            
```

The even function returns true if the number is even

## Relops

```
(<) :: Ord a => a -> a -> Bool
```

| Symbol | Description |
| ----------- | ----------- |
| < | Less than |
| > | Greater than |
| <= | Less than or equal |
| >= | Greater than or equal |
| /= | Not equals |
| == | Yes equals |

```
a `compare` b                    
```

The compare function returns one of: LT, GT, EQ.
Relops can be used on lists

## Boolean operators

```
(&&) :: Bool -> Bool -> Bool
```

| Symbol | Description |
| ----------- | ----------- |
| && | And |
| || | Or |
| not | Not |

## Arithmetic operators

```
(+) :: Num a => a -> a -> a
```
| Symbol | Description |
| ----------- | ----------- |
| `+` | Good ol' addition |
| `-` | Good ol' subtraction |
| `/` | Good ol' division |
| `*` | Good ol' multiplication |
| `**` | Exponentiation with float results |
| `^` | Exponentiation with integer results |
| `mod` | Modulo operator |

## Function declaration and calling

Type declaration (Typeclass has to be replaced with a type):

```
functionName :: Typeclass a => a -> a -> Bool   
```

Function declaration:

```
functionName arg1 arg2 = arg1 == arg2           
```

Infix function declaration:

```
arg1 `infixFunction` arg2 = arg1 + 2 / arg2 
```

Anonymous function:

```
lambdaFunction = (\ arg1 arg2 -> arg1 + arg2)
```

Functions with "special" (the . is one)
characters are automatically infix

The integer next to infxr indicates how tightly the 
function binds. infixr is right associative while 
infixl is left associative.

```
infixr 5 .++                   
(.++) :: [a] ->[a] -> [a]      

[]     .++ ys = ys             
(x:xs) .++ ys = x : (xs ++ ys) 
```

## Variables

```
let variableName = value          -- The let seems to be optional
```

## Lists 

All elements must be of the same types

```
let ls = [1, 2, 3, 4]
let ls1 = ['a', 'b', 'c', 'd']
```

## List operators and basic functions

The following code appends ls1 to ls in a new list.  It errors out
because ls2 is not homogeneous

```
(++) :: [a] -> [a] -> [a]
let ls2 = ls ++ ls1              
```

The following prepends an element (puts it at the beginning):

```
(:) :: a -> [a] -> [a]
let ls2 =  'e': ['c', 'h', 'o'] 
```

In the following *all* becomes another name for the entire list:
useful when breaking up a list with patterns

```
weird :: a -> [a] -> [a]
let weird all@(x:y:ys) = all:ys    
                                   
```

Example of 0-indexed access to an element in a list

```
(!!) :: [a] -> Int -> a
let indexAccess = ls2 !! 2       
```

Head returns the first element of the list

```
head :: [a] -> a
head ls2                     
```

Tail returns all the elements of the list except the first

```
tail :: [a] -> [a]
tail ls                          
```

Last is the last element of a list.

```
last :: [a] -> a
last ls                          
```

Returns all the elements except the last one

```
init :: [a] -> [a]
init ls                         
```

Length returns the length of the list

```
length :: Foldable t => t a -> Int
length ls                            
```

Null returns true if the list is empty

```
null :: Foldable t => t a -> Bool
null                                 
```

*reverse* reverses a list

```
reverse :: [a] -> [a]
reverse                          
```

*take* returns a list of the first x elements of
the list

```
take :: Int -> [a] -> [a]
take 3 ls                        
                                 
```

*drop* returns a list of all the elements except
the first x defined by its argument                        

```
drop :: Int -> [a] -> [a]
drop 3 ls                        
                                 
```

minimum returns the minimum of the entire list

```
minimum :: (Foldable t, Ord a) => t a -> a
minimum ls                       
```

maximum returns the maximum of the entire list

```
maximum :: (Foldable t, Ord a) => t a -> a
maximum ls                       
```

sum returns the summation of the entire list i.e. adds all the elements in ls

```
sum :: (Foldable t, Num a) => t a -> a
sum ls                           
```

product returns the product of all the elements in the list. i.e. multiply all the elements.

```
product :: (Foldable t, Num a) => t a -> a
product ls                       
```

\`elem\` returns True if 1 is in ls

```
elem :: Eq a => a -> [a] -> Bool
1 `elem` ls                      
```

the .. operator returns a list of all integers from x to y

```
[1..20] :: (Num a, Enum a) => [a]
[1..20]                          
```

['a'..'z'] list of chars from 'a' through 'z'

```
['a'..'z'] :: [Char]
['a'..'z']                       
```

[2,4..24] returns a list from 2 to 24 in increments of 2, so 2,4,6,8 and so on

```
[2,4..24] :: (Num a, Enum a) => [a]
[2,4..24]                        
```

Beware! [0.1, 0.3 .. 1] Leads to errors because of how floats work in computers

```
[0.1,0.3 .. 1] :: (Fractional a, Enum a) => [a]
[0.1, 0.3 .. 1]                  
```

cycle repeats a list ad infinitum. Combine with take

```
cycle :: [a] -> [a]
cycle [10, 20]
```

*repeat* makes an infinite list of just 10

```
repeat :: a -> [a]
repeat 10                        
```

*replicate* returns [10 10 10]. Better than combining take with repeat

```
replicate :: Int -> a -> [a]
replicate 3 10                   
```

## List comprehensions

List comprehension: Returns the square of 1 through 10

```
[ x ** 2 | x <- [1..10] ]        
```

Another list comprehension with a condition

```
(Enum a, Floating a) => [a]
[ x*2 | x <- [3..7], x*2 < 6 ]   
```

Longer example of a list comprehension

```
-- :: [[Char]] 
[ if x < 10 then "BOOM!" else "BANG!" | x <- [1..10], odd x] 
```

take returns first 10 odd numbers

```
-- :: Num a => [a]
take 10 [x | x <- [1,2..], odd x]  
```

zipWith (*) [1,3,8] [3,6,9]

```
-- :: Num a => [a]
[ x*y | x <- [1,3,8],y <- [3,6,9]] 
```

## Tuples can mix and match types but have fixed length

A tuple

```
let tuple = (1, 'a', 2.3)         
```

*fst* Returns the first element, a 2

```
fst :: (a, b) -> a
fst (2, 5)                      
```

*snd* returns the second element, an 8

```
snd :: (a, b) -> a
snd (3, 8)                      
```

The following *zip* returns [(1,4), (2,5), (3,6)], a list of tuples

```
zip :: [a] -> [b] -> [(a, b)]
zip [1,2,3] [4,5,6]             
```

## Types

Explicitly typed functions

```
removeNonUppercase :: [Char] -> [Char]
removeNonUppercase str = [ c | c <- str, c `elem` [ 'A'..'Z' ] ]
```

```
addThree :: Int -> Int -> Int -> Int
addThree a b c = a + b + c
```

### Common simple types: 
	
| type | Description |
| ----------- | ----------- |
| Int | 32 or 64 (128?) bit number depending on the system |
| Integer | Same as Int but unbounded size |
| Bool | True or false |
| Char | All one letter characters printable and not |
| Float | Decimal number |
| Double | Larger decimal number double the size of float |
| [Char] | List of chars, a string. [] indicate the list |

```
-- In GHCI use :t to check the type of something
```

### Typeclasses: interface that implements a behavior

```
ghci> :t (==)
(==) :: (Eq a) => a -> a -> Bool  
        ^^^^^^-------------------------- Class constraint
```

## Basic typeclasses

| type | Description |
| ----------- | ----------- |
| Eq | Equality functions like == /= |
| Ord | Order functions < > <= >= |
| Show | Things that can be converted to a string |
| Read | Thing that can be strings and converted to something else |
| Enum | Sequential ordered types |
| Bounded | Have an upper and a lower bound |
| Num | Numerical type |
| Integral | Integers, whole numbers only |
| Floating | Floats and doubles |
| String | Short for [Char]? |

*show* returns "3" as a string

```
show :: Show a => a -> String
show 3             
```

read returns a in the following example: [1, 2, 3]
It tries to find a suitable type for its string argument

```
read :: Read a => String -> a
read "[1, 2, 3]"   
```

```
'a' :: Char        -- type annotation
```

*fromIntegral* converts from integral to Num useful with length
because it returns an integral type

```
(True, 1) :: (Bool, Int)
fromIntegral (length [1,2,3,4]) + 3.2 
```

## Pattern matching

```
lucky :: (Integral a) => a -> String  
lucky 7 = "LUCKY NUMBER SEVEN!"  
lucky x = "Sorry, you're out of luck, pal!"  

sayMe :: (Integral a) => a -> String
sayMe 1 = "One"
sayMe 2 = "Two"
sayMe 3 = "Three"
sayMe 4 = "Four"
sayMe 5 = "Five"
sayMe 6 = "Six"
sayMe 7 = "Seven"
sayMe 8 = "Eight"
sayMe 9 = "Nine"
sayMe x = "Only counting to Nine at this point in time"

factorial :: (Integral a) => a -> a
factorial 0 = 1
factorial n = n * factorial (n - 1)

-- Another factorial function that's tail recursive
fac :: (Integral a) => a -> a -> a
fac 1 c = c
fac n c = fac (n - 1) (c * n)

-- Also works in list comprehensions:
[ a+b | (a,b) <- someListOfTuples ]

head' :: [a] -> a
head' = [] = Error
head' (x:_) = x

-- Example naming the entire pattern 

contrivedMap :: ([a] -> a -> b) -> [a] -> [b]
contrivedMap f [] = []
contrivedMap f list@(x:xs) = f list x : contrivedMap f xs
```

## Guards

```
bmiTell :: (RealFloat a) => a -> String
bmiTell bmi
   | bmi <= 18.5 = "You're probably too skinny"
   | bmi <= 25.0 = "You're balanced"
   | bmi <= 30.0 = "A little overweight"
   | otherwise   = "Time to hit the gym for good health"
```

-- The *where* keyword defines variables whose scope is the previous block

```
-- Better version? Using where
bmiTell :: (RealFloat a) => a -> a -> String
bmiTell weight height
   | bmi <= skinny = "Skinny beach"
   | bmi <= normal = "Normie lute"
   | bmi <= over   = "Over the tap"
   | otherwise     = "Cardio and diet change time baby"
   where bmi = weight / height ^ 2
         skinny = 18.5
         normal = 25.0
         over   = 30.0
```

```
factorial2 :: (Integral a) => a -> a
factorial2 n
    | n < 0 = error "Only non-positives allowed."
    | n == 0 = 1
    | otherwise = fac n 1

-- Let in. Let variables are defined in the following block after the 'in'
[ let square x = x * x in (square 5, square 3, square 2) ]
```

## Conditionals

```
boomBang x = if x < 10 then "boom" else "bang" -- If clause must have an else
```

## Return

```
main :: IO () 
main = do 
   return ()                      -- makes an IO action of a pure value
   return "HAHAHAHA"              -- This gets executed in Haskell
   line <- getLine
   return "LOL                    -- Doesn't stop execution
   return 4
   putStrLn line                  -- Prints the user's input
```
 
## Case

```
{- Syntax of case
case expression of pattern -> result  
                   pattern -> result  
                   pattern -> result  
                   ...
-}
```

```
describeList :: [a] -> String  
describeList xs = "The list is " ++ case xs of [] -> "empty."  
                                               [x] -> "a singleton list."   
                                               xs -> "a longer list."            
```

## $ Dollar Symbol

```
-- It has the lowest precedence and applies the function to its left
-- to the argument on its right, so it's an infix operator.

-- It can be used to replace parentheses...

-- Its definition is:
($) :: (a -> b) -> a -> b
f $ x = f x
```

### Showcasing $'s parens removal capabilities:

Instead of:

```
sum (map sqrt [1..130])
```

You could do:

```
sum $ map sqrt [1..130]
-- Effectively saving you zero keystrokes (counting the spaces)
```

A simple heuristic that seems to work (not proven) is to replace
the left parens with a $.

## Function Composition

Applies the function g to an argument and then applies f to the
output of g with that argument, just like in math.

```
(.) :: (b -> c) -> (a -> b) -> a -> c
f . g = \x -> f (g x)
```

## Importing Modules

Imports the Data.List module:

```
import Data.List                  
```

Only imports nub (filter out reps) and sort:

```
import Data.List (nub, sort)      
```

Imports everything except nub:

```
import Data.List hiding (nub)     
```

Imports but requires Data.Map.filter to call the filter function
for example.  useful to avoid name clashes.

```
import qualified Data.Map         
```

Requires M.filter to call filter.:

```
import qualified Data.Map as M    
```

## Creating Modules

- Step1: create a file with the name of the module

- Step2: use the following syntax. The elements of the tuple are function
names to be defined and when uppercase and with arguments they're types
Must be the FIRST LINE of the file

```
module Geometry
( Shape(Circle, Rectangle)
, Point (..) 
, sphereVolume
, sphereArea
, cubeVolume
, cubeArea
, cuboidArea
, cuboidVolume
) where

sphereVolume :: Float -> Float
sphereVolume radius = (4.0 / 3.0) * pi * (radius ^ 3)

sphereArea :: Float -> Float
sphereArea radius = 4 * pi * (radius ^ 2)

cubeVolume :: Float -> Float
cubeVolume side = cuboidVolume side side side

cubeArea :: Float -> Float
cubeArea side = cuboidArea side side side

cuboidVolume :: Float -> Float -> Float -> Float
cuboidVolume a b c = rectangleArea a b * c

cuboidArea :: Float -> Float -> Float -> Float
cuboidArea a b c = rectangleArea a b * 2 + rectangleArea a c * 2 
                   + rectangleArea c b * 2 

rectangleArea :: Float -> Float -> Float
rectangleArea a b = a * b
```

## Creating sub Modules 

- Step 1 create a directory/folder with the name of the main module

- Step 2 Put the module files in that directory with the following syntax

```
module MainModule.SubModule
( function1
, function2
) where

function1 = "business logic"

function2 = "more business logic"

-- Step 3 import with the normal syntax

import MainModule.SubModule
```

## Module: Data.List

Produces "M.O.N.K.E.Y":

```
intersperse :: a -> [a] -> [a]
intersperse '.' "MONKEY"          
```

Produces "hello, world!":

```
intercalate :: [a] -> [[a]] -> [a]
intercalate ", " ["hello", "world!"]   
```

Produces: [[1,4,7], [2,5,8], [3,6,9]]

```
transpose :: [[a]] -> [[a]]
transpose [[1,2,3], [4,5,6], [7,8,9]]  
```

Use the prime version when the normal foldl causes a stack overflow:

```
foldl' :: Foldable t => (b -> a -> b) -> b -> t a -> b
foldl'                            
```

same as fold' but a plan b for the plan b?:

```
foldl1' :: (a -> a -> a) -> [a] -> a
foldl1'                           
```

Produces "foobarbaz" i.e. flattens a list of lists:

```
concat :: Foldable t => t [a] -> [a]
concat ["foo", "bar", "baz"]      
```

same as composing concat and map. In this example produces
[1,1,1,1,2,2,2,2,3,3,3,3]

```
concatMap :: Foldable t => (a -> [b]) -> t a -> [b]
concatMap (replicate 4) [1..3]    
```

Returns false. Checks if all values are true in a list:

```
and :: Foldable t => t Bool -> Bool
and $ map (> 4) [5,6,3,8]         
```

Returns true. Checks if any value is true, similar to *and* but it's *or*

```
or :: Foldable t => t Bool -> Bool
or $ map (> 4) [5,6,7,3]          
```

Returns true. Checks if any value in the list makes the predicate true

```
any :: Foldable t => (a -> Bool) -> t a -> Bool
any (== 4) [1,3,5,4]              
```

Returns false. Checks if all values make the predicate true

```
all :: Foldable t => (a -> Bool) -> t a -> Bool
all (== 4) [1,2,4,5]              
```

Returns an infinite list where the next element is the result of
the function applied to the current element. In this case, returns
the powers of two

```
take :: Int -> [a] -> [a]
take 10 $ iterate (*2) 1          
```

Returns ("hey", "man"). Splits after the third element

```
splitAt :: Int -> [a] -> ([a], [a])
splitAt 3 "heyman"                
```

Returns [7,8,8] takes while the predicate is true, making a list
with the taken values

```
takeWhile :: (a -> Bool) -> [a] -> [a]
takeWhile (>3) [7,8,8,3,2,1,9]    
```

Returns [4,5,7]. Drops while the predicate is true

```
dropWhile :: (a -> Bool) -> [a] -> [a]
dropWhile (<5) [1,2,3,4,5,7,0]    
```

Returns ([1,2,3,4], [5,6,7]). Combines takeWhile and dropWhile and
returns a tuple with both results.

```
span :: (a -> Bool) -> [a] -> ([a], [a])
span (<5) [1,2,3,4,5,6,7]         
```

Returns ([1,2,3,4], [5,6,7]). So it's the same as span but takes
while the predicate is false

```
break :: (a -> Bool) -> [a] -> ([a], [a])
break (>=5) [1,2,3,4,5,6,7]       
```

Returns [2,3,4,5,6,7]. i.e. it sorts a list. CAVEAT: args must be
part of the Ord typeclass

```
sort :: Ord a => [a] -> [a]
sort [2, 5, 3, 6, 4, 7]           
```

Returns [[2,2],[3,3,3],[4]]. Returns a list with sublist of all
equal elements

```
group :: Eq a => [a] -> [[a]]
group [2,3,3,2,3,4]               
```

Returns [[1,2,3],[1,2],[1],[]].  Recursively applies init to a list
until there's nothing left

```
inits :: [a] -> [[a]]
inits [1,2,3,4]                   
```

Returns [[2,3,4],[3,4],[4],[]]. Recursively applies tail to a list
till there's nothing left

```
tails :: [a] -> [[a]]
tails [1,2,3,4]                   
```

Returns True. Searches for a sublist in a list

```
(isInfixOf) :: Eq a => [a] -> [a] -> Bool
"cat" `isInfixOf` "I'm a cat"     
```

Returns True. Searches for a sublist at the beginning of a list

```
(isPrefixOf) :: Eq a => [a] -> [a] -> Bool
"hey" `isPrefixOf` "hey there!"   
```

Returns False. Searches for asublist at the end of a list

```
(isSuffixOf) :: Eq a => [a] -> [a] -> Bool
"hey" `isSufixOf` "oh hey there!" 
```

Returns True. Checks if the first argument, which is an element,
is in the second argument, which is a list

```
elem :: Eq a => a -> [a] -> Bool
"x" `elem` "Example"              
```

Returns False. The opposite of `elem`, checks if the first argument is not in the second

```
notElem :: Eq a => a -> [a] -> Bool
"S" notElem` "Sample"             
```

Returns ([5,7], [1,3,2]). Creates two
lists the first list includes the elements
that make the predicate true and the second
list is the rest

```
partition :: (a -> Bool) -> [a] -> ([a], [a])
partition (>3) [1,5,3,7,2]        
```

Returns Just 7. Takes a predicate and a list and returns the first
element that makes the predicate true. Returns Nothing otherwise

```
find :: Foldable t => (a -> Bool) -> t a -> Maybe a
find (>5) [1,2,3,7,8]             
```

Returns 2. Returns the index of an elemnt if it is found

```
elemIndex :: Eq a => a -> [a] -> Maybe Int
4 `elemIndex` [1,4,5,6,7]         
```

Returns [2,4,6,8,10]. Returns the indices: of elements that are
equal to the first argument, an element, in the second argument,
which is a list. Returns [] otherwise

```
elemIndices :: Eq a => a -> [a] -> [Int]
' ' `elemIndices` "s p a c e s?"  
```

Returns [(1,3,5), (2,4,6)].  Same as zip joins three through seven
lists putting the elements at the same index in a tuple

```
zip3 :: [a] -> [b] -> [c] -> [(a, b, c)]
zip3 [1,2] [3,4] [5,6]            
zip4 ...                          
...                               
zip7...                           
```

Returns [9, 12]. Same as zipWith joins three through seven lists
given a function to apply to the elements at the same index

```
zipWith3 :: (a -> b -> c -> d) -> [a] -> [b] -> [c] -> [d]
zipWith3 (+) [1,2] [3,4] [5,6]    
zipWith4 ...                      
...                               
zipWith7 ...                      
```

Returns ["1st line", "2nd line]. Breaks up strings on \n, the newline
character

```
lines :: String -> [String]
lines "1st line\n 2nd line"       
```

Returns "1st line\n 2nd line". Takes a : list of strings and breaks
them up with newline characters.

```
unlines :: [String] -> String
unlines ["1st line", "2dn line"]  
```

Returns a list with the words in a sentence.

```
words :: String -> [String]
words "words in a sentence"       
```

Returns "hello mate". Takes a list of strings and joins them with spaces

```
unwords :: [String] -> String
unwords ["hello", "mate"]         
```

Returns [5,1,3,4]. Weeds out duplicates:

```
nub :: Eq a => [a] -> [a]
nub [5,1,3,4,3,1]                 
```

Returns "ey there!". Deletes the first ocurrence of the first
argument

```
delete :: Eq a => a -> [a] -> [a]
delete 'h' "hey there!"           
```

Returns [1,2,3,4,5]. Deletes from the first list, all the elements
that are in the second. Only deletes one per thing in the list.
A.K.A. set difference

```
(\\) :: Eq a => [a] -> [a] -> [a]
([1..10] ++ [5]) \\ [5..15]       
```

Returns [1,2,3,4,5,6,7]. combines two lists and removes duplicates

```
(union) :: Eq a => [a] -> [a] -> [a]
[1..4] `union` [3..7]             
```

Returns [3,4]. Returns only those elements found in both lists. 

```
(intersect) :: Eq a => [a] -> [a] -> [a]
[1..4] `intersect` [3..7]         
```

Returns [3,4,5,1,2]. Inserts an element: into a list in the position before an element that is greater, or at the end of the list

```
(insert) :: Ord a => a -> [a] -> [a]
insert 4 [3,5,1,2]                
```

## Module: Data.List generic versions

Returns 2, the length but is of Num. Which can be used as a float

```
(genericLength) :: Num i => [a] -> i
genericLength [1,2]               
```

Returns [1,2,3,4,5] Same as take but the number to take is of
Integral type

```
(genericTake) :: Integral i => i -> [a] -> [a]
genericTake 5 [1,2,3,4,5,6,7]     
```

Returns [4,5,7] Same as drop but the number to drop is of Integral
type

```
(genericDrop) :: Integral i => i -> [a] -> [a]
genericDrop 3 [1,2,3,4,5,7]       
```

Returns ([1,2,3],[4,5]). Same as splitAt but the number to split
at is of integral type

```
(genericSplitAt) :: Integral i => i -> [a] -> ([a], [a])
genericSplitAt                    
```

Returns 3, the element at index 2. Considering 0 as the first index

```
(genericIndex) :: Integral i => [a] -> i -> a
genericIndex [1,2,3] 2            
                                  
```

Returns [2.3,2.3,2.3] Same as replicate but with Integral type for
the length of the result

```
(genericReplicate) :: Integral i => i -> a -> [a]
genericReplicate 3 2.3            
```

Returns [1,2,3] Same as nub, it dedups the list. However, takes a
user function to test equality

```
(nubBy) :: (a -> a -> Bool) -> [a] -> [a]
nubBy (==) [1,2,2,3,3,3]          
```

Returns [1,2,3,5,4]. Same as delete but takes the functionn to
define equality

```
(deleteBy) :: (a -> a -> Bool) -> a -> [a] -> [a]
deleteBy (==) 4 [1,2,3,4,5,4]     
```

Returns [1,2,3,4]. Same as union but
takes a boolean function to define 
equality

```
(unionBy) :: (a -> a -> Bool) -> [a] -> [a] -> [a]
unionBy (==) [1,2] [3,4]          
```

Returns [2]. Same as intersect but takes
a boolean function

```
(intersectBy) :: (a -> a -> Bool) -> [a] -> [a] -> [a]
intersectBy (==) [1,2]  [2,3]     
```

Returns [[1,1],[2,2],[3]]. Same as group 
but takes a boolean function

```
(groupBy) :: (a -> a -> Bool) -> [a] -> [[a]]
groupBy (==) [1,1,2,2,3]          
```

Returns [1,2,3]. Same as sort but takes a boolean function

```
(sortBy) :: (a -> a -> Ordering) -> [a] -> [a]
sortBy (\a b -> compare a b) [2,3,1]   
```

Returns [2,3,4,1] Same as insert but takes a boolean function

```
(insertBy) :: (a -> a -> Ordering) -> a -> [a] -> [a]
insertBy (\a b -> compare a b) 3 [2,4,1]  
```

Returns 6. Same as maximum but takes a boolean function

```
(maximumBy) :: Foldable t => (a -> a -> Ordering) -> t a -> a
maximumBy (\a b -> compare a b) [2,3,6,1]  
```

Returns 2. Same as minimum but takes a boolean function

```
(minimumBy) :: Foldable t => (a -> a -> Ordering) -> t a -> a
minimumBy (\a b -> compare a b) [3,2,4]  
```

## Module: Data.Char

```
isControl :: Char -> Bool
isControl 'a'                     -- Returns False. Checks whether it is a 
                                  -- control character like for example a kill
                                  -- process signal
```

```
isSpace :: Char -> Bool
isSpace  ' '                      -- Returns True. Checks for space characters
                                  -- including tab 
```

```
isLower :: Char -> Bool
isLower 'a'                       -- Returns True. Lowercase check
```

```
isUpper :: Char -> Bool
isUpper 'A'                       -- Returns True. Uppercase check
```

```
isAlpha :: Char -> Bool
isAlpha 'a'                       -- Returns True. Lower and uppercase 
                                  -- characters of the alphabet
```

```
isAlphaNum :: Char -> Bool
isAlphaNum '5'                    -- Returns True. Checks if the character is 
                                  -- in the alphabet or is a numeral, 0-9
```

```
isPrint :: Char -> Bool
isPrint '\n'                      -- Returns False. Checks if a character
                                  -- can be displayed on the screen
```

```
isDigit :: Char -> Bool
isDigit '4'                       -- Returns True. Checks if a character is 
                                  -- a decimal digit 0-9
```

```
isOctDigit :: Char -> Bool
isOctDigit '8'                    -- Returns False. Checks if the character is 
                                  -- a valid octal system digit, 0-7
```

```
isHexDigit :: Char -> Bool
isHexDigit 'f'                    -- Returns True. Checks if the character is 
                                  -- a hexadecimal digit
```

```
isLetter :: Char -> Bool
isLetter 'c'                      -- Returns True. Checks if the character is
                                  -- a letter? Same as isAlpha?
                                  -- In short and long, yes
```

```
isMark :: Char -> Bool
map isMark "ò"                    -- Returns [False, True]. Checks for 
                                  -- unicode marks, whatever those are
```

```
isNumber :: Char -> Bool
isNumber '5'                      -- Returns True. Checks number same as 
                                  -- isDigit for most intends and purposes. But
                                  -- also selects for Roman numerals and other
                                  -- scripts that have numerals
```

```
isPunctuation :: Char -> Bool
isPunctuation '.'                 -- Returns True. Checks for punctuation
                                  -- characters
```

```
isSymbol :: Char -> Bool
isSymbol '%'                      -- Returns True. Checks for symbols. Includes
                                  -- math symbols and others.
```

```
isSeparator :: Char -> Bool
isSeparator '\t'                  -- Returns False. Checks for separators which
                                  -- include spaces and HTML's &nbsp
```

```
isAscii :: Char -> Bool
isAscii '\b'                      -- Returns True. Checks for ascii characters,
                                  -- the American Standard Code for Information
                                  -- Interchange
```

```
isLatin1 :: Char -> Bool
isLatin1 'a'                      -- "Selects the first 256 characters 
                                  -- of the Unicode character set,
                                  -- corresponding to the ISO 8859-1 
                                  -- (Latin-1) character set."
                                  -- According to 
                                  -- hackage.haskell.org
```

```
isAsciiUpper :: Char -> Bool
isAsciiUpper 'Á'                  -- Returns False. Checks for uppercase AND
                                  -- ascii characters
```

```
isAsciiLower :: Char -> Bool
isAsciiLower 'á'                  -- Returns False. Checks for lowercase aND 
                                  -- ascii characters
```

```
toUpper :: Char -> Char
toUpper 'a'                       -- Returns 'A'. Lower to uppercase
```

```
toLower :: Char -> Char
toLower 'A'                       -- Returns 'a'. Upper to lowercase
```

```
toTitle :: Char -> Char
toTitle 'a'                       -- Returns 'A'. Almost like toUpper except
                                  -- for a subset that I have never heard of.
                                  -- Something about ligatures according to 
                                  -- hackage.haskell.org
```

```
digitToInt :: Char -> Int
digitToInt  '1'                   -- Returns 1. Converts a single diit Char to
                                  -- Int according to hackage.haskell.org
```

```
intToDigit :: Int -> Char
intToDigit 15                     -- Returns 'f'. Returns hexadecimal digits
                                  -- as Chars for numbers 0-15 
```

```
(ord) :: Char -> Int
ord 'a'                           -- Returns 97. Returns the number 
                                  -- corresponding to the byte representation
                                  -- of the Char
```

```
(chr) :: Int -> Char
chr                               -- Returns 'I'. Returns the Char 
                                  -- corresponding to the byte representation
                                  -- of an integer.
```

## Module: Data.Map

```
import qualified Data.Map as Map  -- Good alias for this because of collisions
```

```
Map.fromList [("Fer", "6502292142")] -- Returns a "map", dictionary, associative
                                     --  array. Anything you want to call it
```

```
Data.Map.empty :: Map k a
Map.empty                            -- Returns an Empty hash table. 
                                     -- So many names. Tiny differences. This
                                     -- Map is implemented using a balanced
                                     -- binary tree
```

```
Data.Map.null :: Map k a -> Bool
Map.null Map.empty                   -- Returns True. Checks if the map is empty
```

```
Data.Map.size :: Map k a -> Int
Map.size Map.empty                   -- Returns True. Gets the number of 
                                     -- elements in the map
```

```
Data.Map.singleton :: k -> a -> Map k a
Map.singleton 1 'a'                  -- Returns fromList [(1,'a')] 
                                     -- a singleton Map, one element 
```

```
Data.Map.lookup :: Ord k => k -> Map k a -> Maybe a
Map.lookup 1 (Map.singleton 1 'a')   -- Returns Just 'a'. Looks up a key.
                                     -- returns Nothing if not found
```

```
Data.Map.member :: Ord k => k -> Map k a -> Bool
Map.member 1 (Map.singleton 1 'a')   -- Returns True. Looks up a key and 
                                     -- returns True if found. False otherwise
```

```
Data.Map.map :: (a -> b) -> Map k a -> Map k b
Map.map (+1) (Map.singleton 'k' 55)  -- Returns fromList [('a',56)] 
                                     -- Maps a function over a Map. Confusing,
                                     -- I know. The first map means a function
                                     -- that applies other functions to each
                                     -- of the elements in a data structure.
                                     -- In the case of a Map data structure,
                                     -- the function applies to the value,
                                     -- which is the second element in the 
                                     -- tuple
```

```
Data.Map.filter :: (a -> Bool) -> Map k a -> Map k a
Map.filter (==5) (Map.singleton 'k' 5)   -- Returns fromList ['k' 5].
                                         -- It returns a Map that only
                                         -- contains values that make the
                                         -- predicate function True
```

```
Data.Map.toList :: Map k a -> [(k, a)]
Map.toList Map.toList $ Map.singleton 'k' 1  -- Returns [('k', 5)].
                                             -- Takes a map and returns
                                             -- an equivalent list
```

```
Data.Map.keys :: Map k a -> [k]
Map.keys (fromList [(5, 'a'), (7, 'b')])     -- Returns [5,7]. Takes a Map
                                             -- and returns its keys in a list
```

```
Data.Map.elems :: Map k a -> [a]
Map.elems (fromList [(5,'a'),(7,'b')])        -- Returns "ab". Takes a map and
                                              -- returns its values (elements
                                              -- in their very confusing
                                              -- notation, but mine is also
                                              -- confusing to be honest)
```

```
Data.Map.fromListWith :: Ord k => (a -> a -> a) -> [(k, a)] -> Map k a
Map.fromListWith (++) [(5,"a"), (5,"c"), (3,"b")]  -- Returns fromList
                                                   -- [(3,"b"), (5,"ca")]
                                                   -- Merges elements of the
                                                   -- map that have the same
                                                   -- keys using the function
                                                   -- as a first argument
```

```
Data.Map.insertWith :: Ord k => (a -> a -> a) -> k -> a -> Map k a -> Map k a
Map.insertWith (++) 7 "ol" (fromList [(3,"b"), (7,"l")])  -- Returns
                                                          -- fromList
                                                          -- [(3,"b"),(7,"lol")]
                                                          -- Inserts into the
                                                          -- map and applies
                                                          -- the function when
                                                          -- the key to be 
                                                          -- inserted is already
                                                          -- in the Map
```

## Module: Data.Set

```
import qualified Data.Set as Set  -- Good name

set1 = Set.fromList [1,2,3]
set2 = Set.fromList [2,3,4]
set3 = Set.fromList [5,7,8]
```

```
Data.Set.fromList :: Ord a => [a] -> Set a
Set.fromList [1,2,3,3]            -- Returns fromList [1,2,3]. A set with no
                                  -- repeated elements
```

```
Data.Set.intersection :: Ord a => Set a -> Set a -> Set a
Set.intersection set1 set2        -- Returns fromList [2,3]. Set intersection.
                                  -- Returns a set with all the elements that
                                  -- the two argument sets have in common
```

```
Data.Set.difference :: Ord a => Set a -> Set a -> Set a
Set.difference set1 set2          -- Returns fromList [1]. Returns a set with 
                                  -- the elements of the first set that
                                  -- are not also in the second set
```

```
Data.Set.union :: Ord a => Set a -> Set a -> Set a
Set.union set1 set2               -- Returns fromList [1,2,3,4]. Returns
                                  -- all the elements of the first set and the
                                  -- second, but no repeated elements
```

```
Data.Set.null :: Set a -> Bool
Set.null (Set.fromList [])        -- Returns True. Returns True if the set is
                                  -- empty
```

```
Data.Set.size :: Set a -> Int
Set.size set1                     -- Returns 3,
                                  -- the number of elements in the set
```

```
Data.Set.member :: Ord a => a -> Set a -> Bool
Set.member 3 Set.fromList([1,2,3])  -- Returns True. Checks if an element is
                                    -- in the set
```

```
Data.Set.empty :: Set a
Set.empty                         -- Returns fromList []. Creates an empty
                                  -- set
```

```
Data.Set.singleton :: a -> Set a
Set.singleton 5                    -- Returns fromList [5]. Creates a singleton
                                   -- set 
```

```
Data.Set.insert :: Ord a => a -> Set a -> Set a
Set.insert 5 (Set.singleton 1)    -- Returns fromList [1,5]. Inserts a single 
                                  -- elements to a set, returning a new set
                                  -- that includes that elements and those
                                  -- in the argument set
```

```
Data.Set.delete :: Ord a => a -> Set a -> Set a
Set.delete 3 (Set.fromList [1,3]) -- Returns fromList [1]. Deletes the target
                                  -- element from the set
```

```
Data.Set.map :: Ord b => (a -> b) -> Set a -> Set b
Set.map (+5) (Set.fromList [1,3]) -- Returns fromList [6,8]
                                  -- Apply the argument function to the elements
                                  -- of the set
```

```
Data.Set.toList :: Set a -> [a]
Set.toList set1                   -- Returns [1,2,3]
                                  -- Makes a list from a set

```

## Algebraic Data Types

```
data Bool = False | True

data Int = -214783648| -214783647| ...| -1| 0| 1| ...| 214783646| 214783647

data DataType = ValueConstr1 | ValueConstr2 | ... | ValueConstrN
```

```
data Shape = Circle Float Float Float | Rectangle Float Float Float Float

data Point = Float Float deriving (Show)
data Shape = Circle Point Float| Rectangle Point Point deriving(Show)

data DataType2 = ValueConstructor fiel1 field2 | ValueConstrctr2 field1
data DataType3 = ValueCtr field1 deriving(ExistingDataType, DataType2)
```

```
data RecordSyntaxExample = RecordSyntax { namedField :: String
                                        , namedField2 :: Int
                                        } deriving(Show) -- deriving is optional
```

```
data NewType typedparam = Bad | Good typedParam   -- Take params to create new
                                                  -- types
data Maybe a = Nothing | Just a  -- Maybe is a type constructor. 'Maybe a' is a
                                 -- type because it takes a type as a param
```

```
data List a = Empty | Cons a (List a) deriving (Show, Read, Eq, Ord)
data Tree a = EmptyTree | Node a (Tree a) (Tree a) deriving (Show, Read, Eq) 
```

## Using Algebraic Data Types

```
surface :: Shape -> Float
surface (Circle _ r) = pi * r ^ 2
surface (Rectangle (Point x1 y2) (Point x2 y2) = absDiffX * absDiffY
	where absDiffX = abs $ x2 - x1
          absDiffY = abs $ y2 - y1

RecordSyntaxExample {namedField="some string", namedField2=5}
```

## Algebraic Data Types and Modules

```
module Geometry
( Shape(Circle, Rectangle)        -- You can choose which constructors to add
, Point (..)                      -- Shorthand to add all constructors
, DataType                        -- Doesn't export any constructors
, surface
) where
```

## Type Synonyms

```
type String = [Char]

type AssocList k v = [(k,v)]
```

## Typeclasses

```
class Eq a where 
   (==) :: a -> a -> Bool
   (/=) :: a -> a -> Bool
   x == y = not (x /= y)
   x /= y = not (x == y)
```

```
data TrafficLight = Red | Yellow | Green

instance Eq TrafficLight where
   Red == Red = True
   Green == Green = True
   Yellow == Yellow = True
   _ == _ = False
```

```
class YesNo a where
   yesno :: a -> Bool

instance YesNo Int where
   yesno 0 = False
   yesno _ = True

yesno 0               -- Returns False

yesno 1               -- Returns True

yesno 5               -- Returns True

yesno $ Just 0        -- Returns True
```

This type class can be an enum, that is each Constructor value has a 
predecessor and successor. because all constructors are nullary 
(no parameters). It can also be bounded because there's a least and greatest
Element (If you're like me and think that Monday is less than Friday).
Ord allows us to compare, define greater than or less than.
Eq allows to check for equality

```
data Day = Monday| Tuesday| Wednesday| Thursday| Friday| Saturday| Sunday
```

```
--- class (Eq a) => Num a where     -- This makes it required for a type
--- ...                             -- to derive Eq for it to be a Num as well
```

## Input and output

```
putStrLn :: String -> IO ()       -- Outputs a string on the console
```

```
main = putStrLn "Hello, world!"   -- Puts "Hello,world!" in the console    
                                  -- The main function in a haskell program
                                  -- is always executed?

```

```
getLine :: IO String

main = do
   putStrLn "Hello, what's your name?"
   name <- getLine                           -- <- Takes a IO Something and
   putStrLn ("Hey " ++ name ", you rock!")   -- returns just Something
```

import Data.Char

```
main = do 
   putStrLn "Your name is:"        -- Impure part, the different things for
   name <- getLine                 -- the same input. (this line too)
   let bigName = map toUpper name  -- pure part
   putStrLn bigName                -- impure sort of
```
   
```
main = do
   line <- getLine
   if null line
      then return ()               
      else do
         putStrLn $ reverseWords line
         main
```

```
reverseWords :: String -> String
reverseWords = unwords . map reverse . words
```

```
putStr :: String -> IO ()         -- Same as putStrLn but doesn't append a \n
putStr "Doesn't append a newline"
```

```
putChar :: Char -> IO ()
putChar 'c'                       -- Prints a character, no newline appended
```

```
print :: Show a => a -> IO ()     -- Same as the composition: putStrLn . show
print 2                           -- Calls show and then putStrLn, returning 2
                                  -- so 2 doesn't have to be pre-converted to 
                                  -- a string

```

```
getChar :: IO Char                -- gets a character
c <- getChar
```

```
import Control.Monad   

main = do  
    c <- getChar  
    when (c /= ' ') $ do          -- when executes its second argument when the 
        putChar c                 -- first is True
        main  
```

```
-- when :: Applicative f => Bool -> f () -> f ()

-- sequence :: (Traversable t, Monad m) => t (m a) -> m (t a)
-- Takes a list of IO actions, for example, and returns one IO action
main = do  
    rs <- sequence [getLine, getLine, getLine]  
    print rs 

-- The same as doing this:
main = do  
    a <- getLine  
    b <- getLine  
    c <- getLine  
    print [a,b,c] 

```

```
-- mapM and MapM_ takes an IO action and a list and maps it over the list, then
-- sequences it.

{-
ghci> mapM print [1,2,3]  
1  
2  
3  
[(),(),()]  
ghci> mapM_ print [1,2,3]  
1  
2  
3  
-}
```

### forever :: Applicative f => f a -> f b

```
-- Takes an I/O action and repeats it forever.

import Control.Monad  
import Data.Char  
  
main = forever $ do  
    putStr "Give me some input: "  
    l <- getLine  
    putStrLn $ map toUpper l  

```

```
-- forM is the same as mapM but the arguments are switched around. It makes
-- an I/O action for every element in this list, and then perform those
-- actions and bind their results to something 

import Control.Monad  
  
main = do   
    colors <- forM [1,2,3,4] (\a -> do  
        putStrLn $ "Color you associate with the number: " ++ show a ++ "?"  
        color <- getLine  
        return color)  
    putStrLn "The colors that you associate with 1, 2, 3 and 4 are: "  
    mapM putStrLn colors
```

```
--- getContents takes all the input until EOF 
import Data.Char  
  
main = do  
    contents <- getContents  
    putStr (map toUpper contents) 
```

```
-- interact takes a function. It then gets all the input and passes that input
-- to the function
main = interact shortLinesOnly  
  
shortLinesOnly :: String -> String  
shortLinesOnly input =   
    let allLines = lines input  
        shortLines = filter (\line -> length line < 10) allLines  
        result = unlines shortLines  
    in  result

main = interact $ unlines . filter ((<10) . length) . lines
```

```
-- Open a file and gets its contents
-- openFile :: FilePath -> IOMode -> IO Handle
-- type FilePath = String         -- Just a synonym
-- data IOMode = ReadMode | WriteMode | AppendMode | ReadWriteMode  
import System.IO  
  
main = do  
    handle <- openFile "girlfriend.txt" ReadMode  
    contents <- hGetContents handle  
    putStr contents  
    hClose handle  
```

```
-- Same as before but opens and closes the file for us
import System.IO     
    
main = do     
    withFile "girlfriend.txt" ReadMode (\handle -> do  
        contents <- hGetContents handle     
        putStr contents)  
```

```
-- Same as before but does the binding to a string automatically
import System.IO  
  
main = do  
    contents <- readFile "girlfriend.txt"  
    putStr contents  
```

```
-- Shorthand for opening a file, writing to it (an argument string), and then
-- closing it
import System.IO     
import Data.Char  
    
main = do     
    contents <- readFile "girlfriend.txt"     
    writeFile "girlfriendcaps.txt" (map toUpper contents) 
```

```
-- same as writeFile but it appends rather than truncating it
import System.IO     
    
main = do     
    todoItem <- getLine  
    appendFile "todo.txt" (todoItem ++ "\n")  
```

```
{-
hGetLine, hPutStr, hPutStrLn, hGetChar
work just like their normal counterparts but take handles to output to the
file that's mapped to that handle.
-}
```

```
-- You can control how buffering works with hSetBuffering

main = do   
    withFile "something.txt" ReadMode (\handle -> do  
        hSetBuffering handle $ BlockBuffering (Just 2048)  
        contents <- hGetContents handle  
        putStr contents)  
```

## Random numbers

```
import System.Random              -- This module doesn't come with haskell
main = do  
    gen <- getStdGen  
    putStr $ take 20 (randomRs ('a','z') gen)  
    pptStr $ random
```

```
-- Returns a list of finite random numbers instead of using take.

finiteRandoms :: (RandomGen g, Random a, Num n) => n -> g -> ([a], g)  
finiteRandoms 0 gen = ([], gen)  
finiteRandoms n gen =   
    let (value, newGen) = random gen  
        (restOfList, finalGen) = finiteRandoms (n-1) newGen  
    in  (value:restOfList, finalGen)  

ghci> random (mkStdGen 949488) :: (Float, StdGen)  
(0.8938442,1597344447 1655838864)  
ghci> random (mkStdGen 949488) :: (Bool, StdGen)  
(False,1485632275 40692)  
ghci> random (mkStdGen 949488) :: (Integer, StdGen)  
(1691547873,1597344447 1655838864)  
```

```
-- Getting random numbers at different times:

import System.Random  
  
main = do     
    gen <- getStdGen     
    putStrLn $ take 20 (randomRs ('a','z') gen)     
    gen' <- newStdGen  
    putStr $ take 20 (randomRs ('a','z') gen') 
```

```
-- Little program that asks for random numbers:

import System.Random  
import Control.Monad(when)  
  
main = do  
    gen <- getStdGen  
    askForNumber gen  
  
askForNumber :: StdGen -> IO ()  
askForNumber gen = do  
    let (randNumber, newGen) = randomR (1,10) gen :: (Int, StdGen)  
    putStr "Which number in the range from 1 to 10 am I thinking of? "  
    numberString <- getLine  
    when (not $ null numberString) $ do  
        let number = read numberString  
        if randNumber == number   
            then putStrLn "You are correct!"  
            else putStrLn $ "Sorry, it was " ++ show randNumber  
        askForNumber newGen  
```

## Bytestrings

```
-- Bytestrings are used for reading files in chunks. Useful when the
-- file is extremely large
```

```
-- Functions have the same names as those in Data.List, so it's good
-- to do qualified imports:
import qualified Data.ByteString.Lazy as B  
import qualified Data.ByteString as S  
```

```
-- Lazy bytestrings are evaluated in 64K chunks. This makes them not as 
bad becuase there are fewer chunks.

-- The non-lazy versions use no promises.
import System.Environment  
import qualified Data.ByteString.Lazy as B  
  
main = do  
    (fileName1:fileName2:_) <- getArgs  
    copyFile fileName1 fileName2  
  
copyFile :: FilePath -> FilePath -> IO ()  
copyFile source dest = do  
    contents <- B.readFile source  
    B.writeFile dest contents  
```

## Exceptions

```
-- Catches any types of errors:
import System.Environment  
import System.IO  
import System.IO.Error  
  
main = toTry `catch` handler  
              
toTry :: IO ()  
toTry = do (fileName:_) <- getArgs  
           contents <- readFile fileName  
           putStrLn $ "The file has " ++ show (length (lines contents)) ++ " lines!"  
  
handler :: IOError -> IO ()  
handler e = putStrLn "Whoops, had some trouble!"  
```

### Catches specific errors and then re-throws unknown errors.

```
import System.Environment  
import System.IO  
import System.IO.Error  
  
main = toTry `catch` handler  
              
toTry :: IO ()  
toTry = do (fileName:_) <- getArgs  
           contents <- readFile fileName  
           putStrLn $ "The file has " ++ show (length (lines contents)) ++ " lines!"  
  
handler :: IOError -> IO ()  
handler e  
    | isDoesNotExistError e = putStrLn "The file doesn't exist!"  
    | otherwise = ioError e  
```

### Other error predicates (used to catch errors):

```
isAlreadyExistsError
isDoesNotExistError
isAlreadyInUseError
isFullError
isEOFError
isIllegalOperation
isPermissionError
isUserError
```

### Sources for the correct info.

All the erroneous/bad examples/info were added by me (most likely).

- [hackage](http://hackage.haskell.org)

- [learnyouahaskell](http://learnyouahaskell.com)
