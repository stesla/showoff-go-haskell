!SLIDE center
# Object Orientation #

!SLIDE center
# Favor composition over class inheritance.

!SLIDE center
# Go has no inheritance.

!SLIDE bullets
# Go OO Essentials
* Structs store the data
* Add methods to any type
* Interfaces describe APIs

!SLIDE code
# Struct
    type Point struct {
      x, y float64
    }
    
    var p *Point = new(Point)
    p.x = 3
    p.y = 4

    var p1 Point = Point{3,4}  // Value
    var p2 *Point = &Point{3,4} // Pointer

!SLIDE code
# Methods
    func (self Point) Length() float {
      return math.Sqrt(self.x*self.x + self.y*self.y);
    }

    p := Point{3,4}
    d := p.Length() //=> 5

    /* Note the receiver is *Point */
    func (self *Point) Scale(factor float64) {
      self.x = self.x * factor
      self.y = self.y * factor
    }

    p.Scale(2);
    d = p.Length() //=> 10

!SLIDE code
# Interfaces
    // Somewhere in some code:
    type Widget struct {}
    func (Widget) Frob() { /* do something */ }

    // Somewhere else in the code:
    type Sprocket struct {}
    func (Sprocket) Frob() { /* do something else */ }

    /* New code, and we want to take both Widgets and Sprockets and Frob them */
    type Frobber interface {
      Frob()
    }

    func frobtastic(f Frobber) { f.Frob() }

!SLIDE center
# This is statically checked duck-typing.