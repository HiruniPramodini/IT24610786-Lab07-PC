MPI_Scan should be used when each process needs a cumulative result that includes the values from rank 0 through its own
rank.

For example, it can be used to calculate global offsets for assigning positions or indices to data handled by different
processes. 

MPI_Allreduce is different because it gives the same final global result to every process.
