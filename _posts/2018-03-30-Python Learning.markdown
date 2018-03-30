# Python Learning

> The modification of this post is still ongoing.

## Class

### init, open, new, del and exit
```python
class Vehicle:
    def __init__(self):
        print "Vehicle init"
        pass

    def __open__(self):
        print "Vehicle open"
        pass

    def __new__(cls, *args, **kwargs):
        print "Vehicle new"
        return super(Vehicle, cls).__new__(cls)

    def __enter__(self):
        print "Vehicle enter"
        pass

    def __del__(self):
        print "Vehicle delete"
        pass

    def __exit__(self, exc_type, exc_val, exc_tb):
        print "Vehicle exit"
        pass

Vehicle()

if __name__ == "__main__":

    v = Vehicle()

    with Vehicle() as vv:
       pass
```
Outputs:
> Vehicle init
> Vehicle delete
> Vehicle init
> Vehicle init
> Vehicle enter
> Vehicle exit
> Vehicle delete
> Vehicle delete

