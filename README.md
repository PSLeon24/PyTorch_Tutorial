# PyTorch_Tutorial

## 1. Working with Data
- <b>torch.utils.data.Dataset</b> : Dataset is a fundamental class in PyTorch that helps you manage and access the dataset.
  - Basic Concept
    - The Dataset class serves as an interface for feeding data into your PyTorch model.
    - Regardless of the format of your dataset, you can use the <b>Dataset</b> class by subclassing it and customizing it according to your needs.
    - It allows you to define how to retrieve each data samples and its corresponding labels (target value).
  - Key Methods
    - __len__(self): Returns the number of samples in the dataset.
    - __getitem__(self, idx): Returns the data sample and its corresponding label at the given index.

- Example Code
```
from torch.utils.data import Dataset

class Dataset(Dataset):
    def __init__(self, data, labels):
        self.data = data
        self.labels = labels

    def __len__(self):
        return len(self.data)

    def __getitem__(self, idx):
        sample = self.data[idx]
        label = self.labels[idx]
        return sample, label
```
    
- <b>torch.utils.data.DataLoader</b> : DataLoader takes a Dataset and loads its data, feeding it into your model in mini-batches.
  - Basic Concept
    - It allows you to easily configure the batch size, whether to shuffle the data, and whether to load data in parallel using multiple workers.
  - Key Methods
    - dataset: The Dataset object to load data from.
    - batch_size: Number of samples in each batch.
    - shuffle: If True, the data will be shuffled at the beginning of each epoch.

  - Example Code
```
from torch.utils.data import DataLoader

# Using the Dataset class defined above
dataset = Mataset(data, labels)

# Defining a DataLoader
dataloader = DataLoader(dataset, batch_size=4, shuffle=True, num_workers=2)

# Loading and processing data in batches
for batch_data, batch_labels in dataloader:
    # batch_data and batch_labels each contain 4 samples in this case
    print(batch_data, batch_labels)
```

### References
1. https://pytorch.org/tutorials/
