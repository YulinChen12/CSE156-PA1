# CSE156-PA2 Code 
## Usage
To run the code, execute the `main.py` script with the specified part:

```bash
python main.py [part]
```
Replace ***[part]*** with:
part1

or 

part2
Example Command

To run the Encoder:
```bash
python main.py part1
```
## Dataset Setup

Ensure your dataset files are placed in the data directory with the following structure:
```bash
data/

├── train_CLS.tsv            # Training data for classification

├── test_CLS.txt             # Test data for classification

├── train_LM.txt             # Training data for language modeling

├── test_LM_obama.txt        # Test data for Obama language modeling

├── test_LM_wbush.txt        # Test data for W. Bush language modeling

├── test_LM_hbush.txt        # Test data for H. Bush language modeling
```
