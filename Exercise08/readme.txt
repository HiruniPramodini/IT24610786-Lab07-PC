CC = mpicc
MPIRUN = mpirun
NP = 4

PROGRAMS = program sum_scatter sum_gather sum_reduce sum_allreduce sum_scan

all: $(PROGRAMS)

program: program.c
	$(CC) -o program program.c

sum_scatter: sum_scatter.c
	$(CC) -o sum_scatter sum_scatter.c

sum_gather: sum_gather.c
	$(CC) -o sum_gather sum_gather.c

sum_reduce: sum_reduce.c
	$(CC) -o sum_reduce sum_reduce.c

sum_allreduce: sum_allreduce.c
	$(CC) -o sum_allreduce sum_allreduce.c

sum_scan: sum_scan.c
	$(CC) -o sum_scan sum_scan.c

run: all
	$(MPIRUN) -np $(NP) ./program
	$(MPIRUN) -np $(NP) ./sum_scatter
	$(MPIRUN) -np $(NP) ./sum_gather
	$(MPIRUN) -np $(NP) ./sum_reduce
	$(MPIRUN) -np $(NP) ./sum_allreduce
	$(MPIRUN) -np $(NP) ./sum_scan

clean:
	rm -f $(PROGRAMS)
