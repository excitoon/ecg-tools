Tools for dumping and analyzing ECG data.

# `schiller-dump`

Produces TSV file with Schiller ECG data.

## Usage

```
schiller-dump filename.raw
```

# `myocard-dump`

Produces TSV file with Myocard ECG data.

## Usage

```
myocard-dump data-path
```

# `medilog-dump`

Produces TSV file with SCHILLER medilogAR ECG data (`.MK5` recording).

The format is fully reverse-engineered: container, absolute keyframes, and the per-channel
delta codec (round-robin 4-sample blocks; 6-bit two's-complement deltas / 12-bit absolute
re-anchors at QRS peaks; 10-second segment headers). Decoding is bit-exact — verified against
the vendor's own DARWIN2-rendered waveforms on held-out windows (0 errors over 12600 samples).
A small fraction of super-frames (~0.03%) use a block variant not yet covered and are padded.

## Usage

```
medilog-dump filename.MK5
```

# `ecg-view`

View TSV file (starting at `d:hh:mm:ss`):

```
ecg-view filename.tsv [d:]hh:mm:ss [duration]
```

## Dependencies

```
pip3 install matplotlib
```

# Supported formats

- Schiller MT-101
- МИОКАРД-ХОЛТЕР 2
- SCHILLER medilogAR (`.MK5`)
