# Cyber Apocalypse

# ML

## Enchanted Weights

- The given file was .pth file.
- It is a pytorch file

```python
import torch
torch.set_printoptions(threshold=torch.inf)
checkpoint = torch.load(r"C:\Users\Shawf\Downloads\ml_enchanted_weights\eldorian_artifact.pth")
print("Hello")
print(checkpoint)
```

- 

```python
OrderedDict({'hidden.weight': tensor([[ 72.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.],
        [  0.,  84.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.],
        [  0.,   0.,  66.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.],
        [  0.,   0.,   0., 123.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.],
        [  0.,   0.,   0.,   0.,  67.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.],
        [  0.,   0.,   0.,   0.,   0., 114.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,
           0.,   0.,   0.,   0.],
       
       ....
```

- Then i wrote the code to decode the crystal structure

```python
import torch

torch.set_printoptions(threshold=torch.inf)
checkpoint = torch.load(r"C:\Users\Shawf\Downloads\ml_enchanted_weights\eldorian_artifact.pth")

print("Checkpoint keys:", checkpoint.keys())

# Attempt to extract a flag from the hidden.weight tensor
hidden_tensor = checkpoint.get('hidden.weight')
if hidden_tensor is None:
    print("No hidden.weight key found.")
else:
    # Flatten the tensor to traverse all values
    flat = hidden_tensor.flatten().tolist()
    # Convert tensor value to characters if they map to valid ASCII (range 32-126)
    try:
        flag_chars = ''.join(chr(int(round(x))) for x in flat if 32 <= int(round(x)) <= 126)
        print("Extracted flag (if encoded as ASCII values):", flag_chars)
    except Exception as e:
        print("Error extracting flag:", e)
```

### Flag

![image.png](image.png)

## WasteLand

- I was given a CSV file and a python code to send data to server
- It calculates the reputation score based on all the values of csv file
- I tried to edit my record, but then it got flagged. So i edited others’ and it worked.
- I made the reputation of all to be either 66, 88 except for a few
- Then the corrupt mutations i made them 6,4 or 2
- Then the shadow crimes i made a few 8
- Then i started reducing the dragonfire resistance and reputaion started increasing drastically
- So by trial and error i figured the correct values

[Ashen_Outpost_Records.csv](Ashen_Outpost_Records.csv)

![image.png](5af55c27-de44-48bc-8327-94a9941734c4.png)

### Flag

HTB{4sh3n_D4t4_M4st3r}

---