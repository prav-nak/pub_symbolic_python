### Symbolic computation using custom objects

Basic arithmetic operations in python can easily be extended to custom objects by overriding __op__ functions or **dunder** functions. 
While this might be easy and trivial in some cases, it can be extremely useful in numerical software where the 
math can be done using symolbic expressions and at the end, one can substitute custom objects.  
: for example
```python

# Symbolic math
x = sympy.Symbol('x')
y = sympy.Symbol('y')
expr = str(x * 2 + y ** 2)

# Final substitution
a = CustomModel(np.arange(0, 1000, 10))
b = CustomModel(np.arange(0, 1000, 10))
subs2 = {'x': xval, 'y': yval}
c = eval_expr(str_expr, CustomEvaluator(), subs2)
```

The underlying data in these CustomModels could be numpy arrays. While these operations work for numpy datatypes by default, in compute heavy numerical software 
this is extremely useful and powerful where one can extend to parallel computing using MPI (Message Passing Interface.) Numpy arrays do not perform these arithmetic 
operations in parallel. We can decompose these numpy data in CustomModel and be used for parallel operations.

Run Example.py to see how to use this package. This package is by no means close
to complete, but is a good starting point for my personal use. 

This package is pypi ready: To upload to pypi: 
- ```python
   python setup.py sdist
  ```
- ```python
  pip install twine
  ```
- ```python
  twine upload --repository-url https://test.pypi.org/legacy/ dist/*
  ```
Yes, there is a space before dist in the above command.
