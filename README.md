Caching-the-Inverse-of-a-Matrix
===============================

Caching the Inverse of a Matrix
This function creates an object of a matrix.
makeCacheMatrix <- function(x = matrix()) {
  inv <- NULL
  set <- function(y) {
    x <<- y
    inv <<- NULL
  }
  get <- function() x
  setinverse <- function(inverse) inv <<- inverse
  getinverse <- function() inv
  list(set = set, get = get,
       setinverse = setinverse,
       getinverse = getinverse)
}
 
This function computes the inverse of the matrix returned by above function.
cacheSolve <- function(x, ...) {
  ## Return a matrix that is the inverse of 'x'
  inv <- x$getinverse()
Below step does the check for null values
  if(!is.null(inv)) {
    message("getting cached data")
    return(inv)
  }
  data <- x$get()
Below step solves the equation a %*% x = b for x, where b can be either a vector or a matrix.
  inv <- solve(data, ...)
  x$setinverse(inv)
  inv
}
