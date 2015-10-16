#Get going with go!

###Installing go 1.4
 ```
 git clone https://go.googlesource.com/go $HOME/go1.4;
 cd $HOME/go1.4/src; 
 git checkout release-branch.go1.4;
 ./make.bash;
 ```

###Installing go 1.5 (OBS requires go 1.4 to be installed to bootstrap Go 1.5)
  >Use `./all.bash` instead of `./make.bash` to include runing the unit tests.
  ```
  git clone https://go.googlesource.com/go $HOME/go;
  cd $HOME/go/src;
  git checkout release-branch.go1.5;
  env GO_BOOTSTRAP_ROOT=$HOME/go1.4 ./make.bash;
  ```

###Setup
`export PATH=$PATH:$HOME/go/bin`

###Run
```
package main
 
import "fmt"
 
func main() {
    fmt.Printf("60!\n")
}
```

