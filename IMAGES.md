# Images

## How to convert image files in to [WebP](https://developers.google.com/speed/webp) format

1. Install the WebP CLI, run `brew install webp`.
2. Convert the images you want:
  - Update one image, run `cwebp -q 75 image.png -o image.webp`.
    - The `-q 75` flag refers to "quality of 75%". Meaning the image will be reduced by 25% in "perceivable" quality.
  - Update all images of same extension in a directory, run `find ./ -type f -name '*.png' -exec sh -c 'cwebp -q 75 $1 -o "${1%.png}.webp"' _ {} \;`.
    - Change `.png` in both instances to any other image format (e.g. `.jpg`).
