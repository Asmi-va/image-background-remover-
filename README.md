

---

# Background Removal Script

This Python script uses the `rembg` library to remove the background from an image and saves the output using the `Pillow` (`PIL`) library. 

## Requirements

Ensure the following Python libraries are installed:

- **rembg**: For background removal
- **Pillow**: For image processing

To install these, run:
```bash
pip install rembg Pillow
```

## Usage

1. **Specify Input and Output Paths**  
   Set `input_path` to the path of the input image file and `output_path` to where you want to save the output image (with the background removed).

2. **Run the Script**  
   Run the script in your terminal or IDE. Make sure you have permission to read and write files in the specified directories.

### Code

```python
from rembg import remove
from PIL import Image
import io

input_path = r"C:\path\to\your\input\image.png"  # Replace with your actual input image path
output_path = r"C:\path\to\your\output\output.png"  # Replace with your desired output path

# Open the input image
input_image = Image.open(input_path)

# Remove the background
output_bytes = remove(input_image)

# Convert the result to a PIL Image if necessary
if isinstance(output_bytes, bytes):
    output_image = Image.open(io.BytesIO(output_bytes))
else:
    output_image = output_bytes

# Save the output image
output_image.save(output_path)
print(f"Output saved at {output_path}")
```

## Troubleshooting

- **Output Not Saving**: If the output is not saving, check:
  - File permissions in the output directory.
  - Ensure `output_path` is set to a directory where you have write access.
  - Verify that the `rembg` library is returning a valid `PIL.Image` object.

## Notes

- **Supported Image Formats**: The script supports common image formats (e.g., `.png`, `.jpg`). PNG format is recommended for images with transparent backgrounds.
- **Compatibility**: This script is compatible with Python 3.x versions.

## License

This project is licensed under the MIT License.

---

