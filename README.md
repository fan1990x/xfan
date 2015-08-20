# xfan
#create a special matrix
makeCacheMatrix<- function(x=matrix()){
  m<- NULL
  set<- function(y) {
    x<<- y
    m<<- NULL
  }
  get<- function() x
  setinverse <- function(inverse) m<<- inverse
  getinverse <- function() m
  list(set=set, get=get, setinverse=setinverse, getinverse=getinverse)
}

#get inverse of makeCacheMatrix

cacheSolve<- function(x, ...) {
  m<- x$getinverse()
  if(!is.null(m)){
    message("getting cahched data")
    return(m)
  }
data<-x$get()
m<-solve(data,...)
x$setinverse(m)
m
}
