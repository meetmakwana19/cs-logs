# Installing `mdbook` on windows :

1. Download rust setup file n install it via visual studio installer.
2. Check rust and cargo versions.
```
rustc --version
cargo --version
```
3. Install mdbook
```
cargo install mdbook
```
4. Initiate a mdbook
```
mdbook init
```
5. Render the book
```
mdbook build
```
6. Run web server to view the book, and rebuild on changes.
```
mdbook serve 
```