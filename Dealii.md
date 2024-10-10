[[C++]]

- [x] step-1 ✅ 2024-05-21
	- [x] Creating mesh 1 ✅ 2024-05-21
		main takeaway: Fill the triangulation with a single cell for a square domain. The triangulation is the refined 4 times, to yield $4^4=256$ cells in total:
		`GridGenerator::hyper_cube(triangulation);
		`triangulation.refine_global(4);
	- [x] creating mesh 2 ✅ 2024-05-21
		main takeaway: quadrilaterals are only used in Dealii. Refinement towards inner radius was created using a custom function someone made and we just call 
- [ ] [[step-2]]
	- [ ] degrees of freedom
		Main takeaway: degrees of freedom are located at cell nodes
		
- [ ] step-3
	- [ ] integration by parts
- [ ] step-4
- [ ] step-5
- [ ] step-6
- [ ] step-7
- [ ] step-8
- [ ] step-9
- [ ] step-10
- [ ] step-11
- [ ] step-12
- [ ] step-13
- [ ] step-14
- [ ] step-15
- [ ] step-16
- [ ] step-17
- [ ] step-18
- [ ] step-19
- [ ] step-20
- [ ] step-21
- [ ] step-22