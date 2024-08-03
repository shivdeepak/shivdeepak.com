+++
title = "Let's create subarrays"
date = 2024-08-01T09:59:53-07:00
description = "This post covers how to creat sub arrays in Python, Ruby and Javascript"
draft = false
type = "post"


+++

I code in atleast 3-4 programming languages regularly, and I often mix up Ruby, Python, and JavaScript syntax. To help keep things organized and provide a quick reference, I'm planning a series of articles that outline common functionalities in these languages.

In this article, I’ll cover creating subarrays in Python, Ruby and Javascript. The idea is to create a writup that keeps everything in one place.

So, here we go.

### Slice an array with begining index and end index

Begining will be inclusive, and end will be exclusive. This is the most common way to slice an array in almost all programming languages.

**Python**

```python
array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
start = 3
end = 8
print(array[start:end])
# [4, 5, 6, 7, 8]
```

**Ruby**

```ruby
array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
start = 3
ending = 8
print(array[start...ending]) # note three dots
# [4, 5, 6, 7, 8] => nil
```

**Javascript**

```javascript
array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
start = 3
end = 8
console.log(array.slice(start, ending))
// [ 4, 5, 6, 7, 8 ]
// undefined
```

That's it, this is all you need to know. Now if you want to get fancy, there are more ways to slice an array in Python and Ruby.

**Python: Use Negative Indexes**

Using Negative indexes can be nice if you want to operate towards the rear of a list, and not so much towards the front. Infact, you can mix and match if you like. Negative indexes work the following way.

```python
negative_index = postive_index - array_length
```

So, to get the last element in an array. You can simply do:

```python
array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(array[-1])
# 10
```

And if you want to do subarray

```python
array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
start = -7 # == 3 - 10 == 3 - len(array)
end = -2 # == 8 - 10 == 8 - len(array)
print(array[start:end])
# [4, 5, 6, 7, 8]
```

Note that it's helpful if you are indexing from the rear of an array, and the index starts with `-1`.

**Ruby: Use 2-dot (`..`) operation**

Ruby has a 2-dot `..` array slice operation along with 3-dot `...`. The only difference between the two is 2-dot is inclusive, and 3-dot is rear exclusive.

Example:
```ruby
array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
start = 3
ending = 8
print(array[start...ending]) # note three dots
# [4, 5, 6, 7, 8] => nil

start = 3
ending = 7
print(array[start..ending]) # note two dots
# [4, 5, 6, 7, 8] => nil
```

### Conclusion

For consistency, I recommend going with the standard slicing approach with start inclusive, and end exclusive.

In cases when you find yourself working on the rear of the array a lot in python. You can use negative indexing in Python.
