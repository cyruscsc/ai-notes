## Defintion

- Applying a filter that add each pixel value of an image to its neighbours, weighted according to a kernel matrix
- Doing so alters the image and can help the neural network process it

## Benefits 

### Translation invariance

- Helps recognizing a pattern regardless of where it is in the picture

### Locality

- Processes local pixels together to spot local pattern

### Reduction in weights

- Reduces number of weights required to train
- Copies of the same filter use the same weight

## Common kernels

> Note: use multiple kernels/filters to detect different patterns

### Edge detection

$$
\begin{bmatrix}
-1&-1&-1\\
-1&8&-1\\
-1&-1&-1
\end{bmatrix}
$$

- When the pixel is similar to all its neighbours, they cancel each other, giving a value of 0
- The more similar the pixels, the darker the part of the image
- The more different the pixels, the lighter the part of the image

## Example

### Image

$$
\begin{bmatrix}
10&20&30&40\\
10&20&30&40\\
20&30&40&50\\
20&30&40&50
\end{bmatrix}
$$

### Kernel

$$
\begin{bmatrix}
0&-1&0\\
-1&5&-1\\
0&-1&0
\end{bmatrix}
$$

### Result

$$
\begin{bmatrix}
10&20\\
40&50
\end{bmatrix}
$$

## Code example

```python
import math
import sys

from PIL import Image, ImageFilter

# Ensure correct usage
if len(sys.argv) != 2:
  sys.exit("Usage: python filter.py filename")

# Open image
image = Image.open(sys.argv[1]).convert("RGB")

# Filter image according to edge detection kernel
filtered = image.filter(ImageFilter.Kernel(
  size=(3, 3),
  kernel=[-1, -1, -1, -1, 8, -1, -1, -1, -1],
  scale=1
))

# Show resulting image
filtered.show()
```