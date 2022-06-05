1.
    a. h(x) = x + 17 is NOT a hash function because, given arbitrary number of inputs, output of the hash function should be the same size.
    
    b. g(x) = (x+17)mod1024, this function violates pre-image resistance and collision resistance,  for instance, when if x = 0, result will be 17 , then x = 1024, result will be 17 as well. Given two different values should not procude same output. 

    
