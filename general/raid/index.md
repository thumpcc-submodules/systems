# RAID

[RAID](https://en.wikipedia.org/wiki/RAID)  ("redundant array of independent disks" or "redundant array of inexpensive disks") is a data
storage virtualization technology that combines multiple physical disk drive components into one or more logical units
for the purposes of data redundancy, performance improvement, or both.

It employs the techniques of striping, mirroring, or parity to create large reliable data stores from multiple
general-purpose computer disk drives.


## Standard RAID levels

Originally, there were five [standard levels of RAID](https://en.wikipedia.org/wiki/Standard_RAID_levels), but many variations have evolved,
including several nested levels and many non-standard levels (mostly proprietary). RAID levels and their associated data
formats are standardized by the Storage Networking Industry Association (SNIA) in the Common RAID Disk Drive Format (
DDF) standard.

**RAID 0 (striping)**

``````{grid}

`````{grid-item}

[RAID 0](https://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_0) (also known as a stripe set or striped volume) splits ("stripes") data evenly across two or more disks, without parity information, redundancy, or fault tolerance.

`````
`````{grid-item}
:columns: auto

```{image} https://upload.wikimedia.org/wikipedia/commons/9/9b/RAID_0.svg
:height: 222px
```

`````
``````

**RAID 1 (mirroring)**

``````{grid}
`````{grid-item}

[RAID 1](https://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_1) consists of an exact copy (or mirror) of a set of data on two or more disks; a classic RAID 1 mirrored pair contains two disks.

`````
`````{grid-item}
:columns: auto

```{image} https://upload.wikimedia.org/wikipedia/commons/b/b7/RAID_1.svg
:height: 222px
```

`````
``````

**RAID 2**

``````{grid}

`````{grid-item}
[RAID 2](https://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_2) which is rarely used in practice, stripes data at the bit (rather than block) level, and uses a Hamming code for error correction
`````
`````{grid-item}
:columns: auto

```{image} https://upload.wikimedia.org/wikipedia/commons/b/b5/RAID2_arch.svg
:height: 222px
```

`````
``````

**RAID 3**

``````{grid}

`````{grid-item}
[RAID 3](https://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_3) which is rarely used in practice, consists of
byte-level striping with a dedicated parity disk. One of the characteristics of RAID 3 is that it generally cannot
service multiple requests simultaneously, which happens because any single block of data will, by definition, be spread
across all members of the set and will reside in the same physical location on each disk.
`````
`````{grid-item}
:columns: auto

```{image} https://upload.wikimedia.org/wikipedia/commons/f/f9/RAID_3.svg
:height: 222px
```

`````
``````

**RAID 4**

``````{grid}

`````{grid-item}
[RAID 4](https://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_4) consists of block-level striping with a dedicated
parity disk. As a result of its layout, RAID 4 provides good performance of random reads, while the performance of
random writes is low due to the need to write all parity data to a single disk,[21] unless the filesystem is
RAID-4-aware and compensates for that.
`````
`````{grid-item}
:columns: auto

```{image} https://upload.wikimedia.org/wikipedia/commons/a/ad/RAID_4.svg
:height: 222px
```

`````
``````

**RAID 5 (distributed parity)**

``````{grid}

`````{grid-item}
[RAID 5](https://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5) consists of block-level striping with distributed
parity. Unlike in RAID 4, parity information is distributed among the drives. It requires that all drives but one be
present to operate. Upon failure of a single drive, subsequent reads can be calculated from the distributed parity such
that no data is lost. RAID 5 requires at least three disks.
`````
`````{grid-item}
:columns: auto

```{image} https://upload.wikimedia.org/wikipedia/commons/6/64/RAID_5.svg
:height: 222px
```

`````
``````

**RAID 6 (dual parity)**

``````{grid}

`````{grid-item}
[RAID 6](https://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_6) extends RAID 5 by adding another parity block; thus,
it uses block-level striping with two parity blocks distributed across all member disks.

As in RAID 5, there are many layouts of RAID 6 disk arrays depending upon the direction the data blocks are written, the
location of the parity blocks with respect to the data blocks and whether or not the first data block of a subsequent
stripe is written to the same drive as the last parity block of the prior stripe.
`````
`````{grid-item}
:columns: auto

```{image} https://upload.wikimedia.org/wikipedia/commons/7/70/RAID_6.svg
:height: 222px
```

`````
``````

## Nested RAID

[Nested RAID levels](https://en.wikipedia.org/wiki/Nested_RAID_levels), also known as hybrid RAID, combine two or more of the [standard RAID levels](#standard-raid-levels) (where "RAID" stands for "redundant array of independent disks") to gain performance, additional redundancy or both, as a result of combining properties of different standard RAID layouts.


**RAID 01 (RAID 0+1)**

[RAID 01](https://en.wikipedia.org/wiki/Nested_RAID_levels#RAID_01_(RAID_0+1)), also called RAID 0+1, is a RAID level using a mirror of stripes, achieving both replication and sharing of data between disks. The usable capacity of a RAID 01 array is the same as in a RAID 1 array made of the same drives, in which one half of the drives is used to mirror the other half.

```{image} https://upload.wikimedia.org/wikipedia/commons/a/ad/RAID_01.svg
```

**RAID 03 (RAID 0+3)**

[RAID 03](https://en.wikipedia.org/wiki/Nested_RAID_levels#RAID_03_(RAID_0+3)), also called RAID 0+3 and sometimes RAID 53, is similar to RAID 01 with the exception that byte-level striping with dedicated parity is used instead of mirroring.

```{image} https://upload.wikimedia.org/wikipedia/commons/0/0f/RAID_0%2B3.svg
```

**RAID 10 (RAID 1+0)**

[RAID 10](https://en.wikipedia.org/wiki/Nested_RAID_levels#RAID_10_(RAID_1+0)), also called RAID 1+0 and sometimes RAID 1&0, is similar to RAID 01 with an exception that the two used standard RAID levels are layered in the opposite order; thus, RAID 10 is a stripe of mirrors.

```{image} https://upload.wikimedia.org/wikipedia/commons/e/e6/RAID_10_01.svg
```

**RAID 50 (RAID 5+0)**

[RAID 50](https://en.wikipedia.org/wiki/Nested_RAID_levels#RAID_50_(RAID_5+0)), also called RAID 5+0, combines the straight block-level striping of RAID 0 with the distributed parity of RAID 5.[3] As a RAID 0 array striped across RAID 5 elements, minimal RAID 50 configuration requires six drives. On the right is an example where three collections of 120 GB RAID 5s are striped together to make 720 GB of total storage space.

```{image} https://upload.wikimedia.org/wikipedia/commons/9/9d/RAID_50.png
```

**RAID 60 (RAID 6+0)**

[RAID 60](https://en.wikipedia.org/wiki/Nested_RAID_levels#RAID_60_(RAID_6+0)), also called RAID 6+0, combines the straight block-level striping of RAID 0 with the distributed double parity of RAID 6, resulting in a RAID 0 array striped across RAID 6 elements. It requires at least eight disks.

```{image} https://upload.wikimedia.org/wikipedia/commons/0/0d/RAID_60.png
```

**RAID 100 (RAID 10+0)**

[RAID 100](https://en.wikipedia.org/wiki/Nested_RAID_levels#RAID_100_(RAID_10+0)), sometimes also called RAID 10+0, is a stripe of RAID 10s. This is logically equivalent to a wider RAID 10 array, but is generally implemented using software RAID 0 over hardware RAID 10. Being "striped two ways", RAID 100 is described as a "plaid RAID"

```{image} https://upload.wikimedia.org/wikipedia/commons/c/ce/RAID_100.svg
```

## External Links

- https://en.wikipedia.org/wiki/RAID
- https://en.wikipedia.org/wiki/Standard_RAID_levels
- https://en.wikipedia.org/wiki/Nested_RAID_levels
