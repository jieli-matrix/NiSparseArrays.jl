# NiSparseArrays

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://jieli-matrix.github.io/NiSparseArrays.jl/stable)
[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://jieli-matrix.github.io/NiSparseArrays.jl/dev)
[![Build Status](https://github.com/jieli-matrix/NiSparseArrays.jl/workflows/CI/badge.svg)](https://github.com/jieli-matrix/NiSparseArrays.jl/actions)
[![Coverage](https://codecov.io/gh/jieli-matrix/NiSparseArrays.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/jieli-matrix/NiSparseArrays.jl)

[中文版本](README_CN.md)

This is a repository for the Summer 2021 of Open Source Promotion Plan. NiSparseArrays implements operations in [SparseArrays](https://docs.julialang.org/en/v1/stdlib/SparseArrays/) in a reversible way by [NiLang](https://giggleliu.github.io/NiLang.jl/dev/). 

## Background 

Sparse matrices are extensively used in scientific computing, however there is no automatic differentiation package in Julia yet to handle sparse matrix operations yet. This project will utilize the reversible embedded domain-specific language NiLang.jl to differentiate sparse matrix operations by re-writing the sparse functions in Julia base in a reversible style. Furthermore, the generated backward rules would be generated to ChainRules.jl as an extension.

## Install 

``` shell
git clone https://github.com/jieli-matrix/NiSparseArrays.jl.git
# git clone https://gitlab.summer-ospp.ac.cn/summer2021/210370152.git
```

To install, type ] in a julia (>=1.6) REPL and then input

``` julia
pkg> add NiSparseArrays 
```

## API References  

| API             | description        |
| ---------------- | --------------- |
| `function imul!(C::StridedVecOrMat, A::AbstractSparseMatrix{T}, B::DenseInputVecOrMat, α::Number, β::Number) where T`   | sparse matrix to dense matrix multiplication |
|`function imul!(C::StridedVecOrMat, xA::Adjoint{T, <:AbstractSparseMatrix}, B::DenseInputVecOrMat, α::Number, β::Number) where T` |  adjoint sparse matrix to dense matrix multiplication |
|`function imul!(C::StridedVecOrMat, X::DenseMatrixUnion, A::AbstractSparseMatrix{T}, α::Number, β::Number) where T`| dense matrix to sparse matrix multiplication |
|`function imul!(C::StridedVecOrMat, X::Adjoint{T1, <:DenseMatrixUnion}, A::AbstractSparseMatrix{T2}, α::Number, β::Number) where {T1, T2}`| adjoint dense matrix to sparse matrix multiplication |
|`imul!(C::StridedVecOrMat, X::DenseMatrixUnion, xA::Adjoint{T, <:AbstractSparseMatrix}, α::Number, β::Number) where T`|dense matrix to sparse matrix multiplication |
|`function idot(r, x::AbstractVector, A::AbstractSparseMatrix{T1}, y::AbstractVector{T2}) where {T1, T2}` | dot operation between sparsematrix and densevector|
|`function idot(r, x::SparseVector, A::AbstractSparseMatrix{T1}, y::SparseVector{T2}) where {T1, T2}`| dot operation between sparsematrix and sparsevector|

More to add in the next stage...

## Contribute 

Suggestions and Comments in the Issues are welcome.

## License

MIT License
