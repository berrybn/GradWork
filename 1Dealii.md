[[📕 C++]]
# Tutorials
- [x] [[step-1]] ✅ 2024-05-24
	- [x] Step 1 annotations 🛫 2024-06-06 ✅ 2024-06-10 [[step-1]]
	- [x] Creating mesh 1 ✅ 2024-05-24
		main takeaway: Fill the triangulation with a single cell for a square domain. The triangulation is the refined 4 times, to yield $4^4=256$ cells in total:
		`GridGenerator::hyper_cube(triangulation);
		`triangulation.refine_global(4);
	- [x] creating mesh 2 ✅ 2024-05-24
		main takeaway: quadrilaterals are only used in Dealii. Refinement towards inner radius was created using a custom function someone made and we just call, refinement over active cells 
- [x] [[step-2]] ✅ 2024-05-30
	- [x] Step 2 annotations 🛫 2024-06-06 [[step-2]] ✅ 2024-06-16
	- [x] [[degrees of freedom]] ✅ 2024-05-30
		main takeaway: degrees of freedom are found by enumerating the mesh nodes or later, enumerating the shape functions associated with the edges, faces, or cell interiors of the mesh
		- The enumerated degrees of freedom, however, are an entirely separate thing from the indices that we will use to number the vertices of the mesh.
		- answers "how many DoF are there, globally?"
	- [x] [[shape functions]] ✅ 2024-05-30
		main takeaway: the shape function is the function which interpolates the solution between the discrete values obtained at the mesh nodes. ==We will use the [[Legendre Polynomials]] for our shape function, moving forward.== 
		- [x] [[monomial basis]] ✅ 2024-05-30
	- [x] [[sparsity]]  ✅ 2024-06-10
		main takeaway: sparsity happens by construction, and we take advantage of that so we can solve larger systems of equation
- [x] [[step-3]] ✅ 2024-06-20
	- [x] 3 annotations🛫 2024-06-06 [[step-3]] ✅ 2024-06-18
	- [ ] [[partial differentiation]]
	- [ ] [[📕 Finite Element Method]]
- [x] [[step-4]] ✅ 2024-06-20
	- [x] step 4 annotations 📅 2024-06-20 ✅ 2024-06-20
- [ ] [[Mohebujjman Research Problem]]