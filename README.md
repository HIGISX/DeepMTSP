# BiGNN:  Bipartite Graph Neural Network with Attention Mechanism for Solving Multiple Traveling Salesman Problems in Urban Logistics

This project is the code for the study: 

Liang, H., Wang, S., Li, H., Zhou, L., Zhang, X., & Wang, S. (2024). BiGNN: Bipartite graph neural network with attention mechanism for solving multiple traveling salesman problems in urban logistics. International Journal of Applied Earth Observation and Geoinformation, 129, 103863.[[Full article]](https://www.sciencedirect.com/science/article/pii/S1569843224002176)

Paper reference:
```bash
@article{liang2024bignn,
  title={BiGNN: Bipartite graph neural network with attention mechanism for solving multiple traveling salesman problems in urban logistics},
  author={Liang, Haojian and Wang, Shaohua and Li, Huilai and Zhou, Liang and Zhang, Xueyan and Wang, Shaowen},
  journal={International Journal of Applied Earth Observation and Geoinformation},
  volume={129},
  pages={103863},
  year={2024},
  publisher={Elsevier}
}
```

## Installation

See installation instructions [here](INSTALL.md).

## Running the experiments
```
# Generate MILP instances
python 01_generate_instances.py Standard_MTSP
python 01_generate_instances.py MinMax_MTSP
python 01_generate_instances.py Bounded_MTSP
```

### Standard_MTSP(2W Training set)
```
# Generate supervised learning datasets
python 02_generate_datasets.py Standard_MTSP -j 4  # number of available CPUs
# Training
for i in {0..4}
do
    python 03_train_gcnn.py Standard_MTSP -m baseline -s $i
    python 03_train_gcnn.py Standard_MTSP -m attention -s $i
    python 03_train_competitor.py Standard_MTSP -m extratrees -s $i
    python 03_train_competitor.py Standard_MTSP -m svmrank -s $i
    python 03_train_competitor.py Standard_MTSP -m lambdamart -s $i
done
# Test
python 04_test.py MTSP_ori
```

### Standard_MTSP(10W Training set)
```
# Generate supervised learning datasets
python 02_generate_datasets.py Standard_MTSP_10w -j 4  # number of available CPUs
# Training
for i in {0..4}
do
    python 03_train_gcnn.py Standard_MTSP_10w -m baseline -s $i
    python 03_train_gcnn.py Standard_MTSP_10w -m attention -s $i
    python 03_train_competitor.py Standard_MTSP_10w -m extratrees -s $i
    python 03_train_competitor.py Standard_MTSP_10w -m svmrank -s $i
    python 03_train_competitor.py Standard_MTSP_10w -m lambdamart -s $i
done
# Test
python 04_test.py Standard_MTSP_10w
```
### MinMax_MTSP（2W Training set）
```
# Generate supervised learning datasets
python 02_generate_datasets.py MinMax_MTSP -j 4  # number of available CPUs
# Training
for i in {0..4}
do
    python 03_train_gcnn.py MinMax_MTSP -m baseline -s $i
    python 03_train_gcnn.py MinMax_MTSP -m attention -s $i
    python 03_train_competitor.py MinMax_MTSP -m extratrees -s $i
    python 03_train_competitor.py MinMax_MTSP -m svmrank -s $i
    python 03_train_competitor.py MinMax_MTSP -m lambdamart -s $i
done
# Test
python 04_test.py MinMax_MTSP
```

### MinMax_MTSP（10W Training set）
```
# Generate supervised learning datasets
python 02_generate_datasets.py MinMax_MTSP_10w -j 4  # number of available CPUs
# Training
for i in {0..4}
do
    python 03_train_gcnn.py MinMax_MTSP_10w -m baseline -s $i
    python 03_train_gcnn.py MinMax_MTSP_10w -m attention -s $i
    python 03_train_competitor.py MinMax_MTSP_10w -m extratrees -s $i
    python 03_train_competitor.py MinMax_MTSP_10w -m svmrank -s $i
    python 03_train_competitor.py MinMax_MTSP_10w -m lambdamart -s $i
done
# Test
python 04_test.py MinMax_MTSP
```

### Bounded_MTSP（2W Training set）
```
# Generate supervised learning datasets
python 02_generate_datasets.py Bounded_MTSP -j 4  # number of available CPUs
# Training
for i in {0..4}
do
    python 03_train_gcnn.py Bounded_MTSP -m baseline -s $i
    python 03_train_gcnn.py Bounded_MTSP -m attention -s $i
    python 03_train_competitor.py Bounded_MTSP -m extratrees -s $i
    python 03_train_competitor.py Bounded_MTSP -m svmrank -s $i
    python 03_train_competitor.py Bounded_MTSP -m lambdamart -s $i
done
# Test
python 04_test.py Bounded_MTSP
```

### Bounded_MTSP（10W Training set）
```
# Generate supervised learning datasets
python 02_generate_datasets.py Bounded_MTSP_10w -j 4  # number of available CPUs
# Training
for i in {0..4}
do
    python 03_train_gcnn.py Bounded_MTSP_10w -m baseline -s $i
    python 03_train_gcnn.py Bounded_MTSP_10w -m attention -s $i
    python 03_train_competitor.py Bounded_MTSP_10w -m extratrees -s $i
    python 03_train_competitor.py Bounded_MTSP_10w -m svmrank -s $i
    python 03_train_competitor.py Bounded_MTSP_10w -m lambdamart -s $i
done
# Test
python 04_test.py Bounded_MTSP_10w
```

## Citation
Please cite our paper if you use this code in your work.


