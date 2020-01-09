# spatial-encoding

## About

This script is a visual demonstration of a specialized spatial codec algorithm developed for mapping a 1D bitarray to a 3D matrix with a specified dimension. The encoder takes a 1D bitarray and translates each bit to an equivalent set of 'spatial bits' consisting of a coordinate tuple [x,y,z] and a state (True or False) attribute. The encoding is mapped using Hilbert's space filling curve (https://en.wikipedia.org/wiki/Hilbert_curve) which preserves localized bits in 1D to geometry in 3D independant of the matrix dimension.

This mapping allows for consistent network packing/unpacking protocols independent of the cube dimensions. Furthermore it ensures that if a particular localized region of the 3D space is obstructed or is unreadable then the corresponding bit data errors will be localized to a set of neighbouring bits in 1D space which effectively reduces the severity of error across the whole message.

## Setup

Install the following modules to enable plotting functionality:
```
pip install plotly
```
```
pip install pandas
```
Install the following module to enable the bitarray generation:
```
pip install bitarray
```
## Run

The script takes in 2 input arguments: the first is the matrix dimension (must be a power of 2) and the second is for the number of random 1D bitarray frames the algorithm will generate.

The following example will generate 32 frames on a 4x4x4 matrix map:
```
python spatial_encoder.py 4 32
```
Once the script completes it will generate a 'plotly' figure using your native browser. The initial frame will show a superposition of spatial bit mapping for all generated frames. Using the slider you can view a specific frames spatial mapping. Each point represents a bit that is has a state=True. The connecting lines follow the sequence in which the 1D bitarray constructs the 3D spatial bit map. By default each frame starts at point (0,0,0) and terminates at (0,0,3).

## License

This project is licensed under the MIT License - see the LICENSE.md file for details
