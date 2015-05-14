# NLopt-failure
An example where NLopt fails to find the solution of a well defined convex problem.

This pdf summarizes the problem that I am considering. It concerns utility maximization subject to a static budget constraint. The major difference from standard utility max problems is that in this case there are many consumption goods (rather than one single commodity): as a result NLopt needs to optimize the utility function with respect to many variables. 

I am considering two NLopt algorithms, a gradient based one (SLSQP) and another that is derivative free (COBYLA). Both succeed in finding the optimal when the scale of the problem, determined by the scale of available income, is small (say, income = 10). But both fail to find a solution when income is scaled up (say, income = 100 or income == 900). Even if one pushes the tolerance criterion to extreme values (say 1e-16) NLopt fails to find the true optimal point (i.e. the one that satisfies the FOCs and the constraint).

Open main.jl and run doNlopt() to see the results from the gradient-based algorithm. You can then change that to the derivative-free algorithm (in funs.jl) and run again. (For the time being I ignore the fact that one can rewrite the objective incorporating the constraint in it).
