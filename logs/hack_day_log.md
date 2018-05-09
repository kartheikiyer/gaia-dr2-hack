# Rutgers Gaia DR2 Hack (9th May 2018)

Notes from today's work.

## Data:

For the problems I'm interested in working on (fraction of 2 and 3 star systems, tidal streams etc.), I would like the subset of the data that I'm working on to be as representative of the full data as possible. To this end, I'm querying the dr2 data by `random_index` (see more [here](https://gea.esac.esa.int/archive/documentation/GDR2/Gaia_archive/chap_datamodel/sec_dm_main_tables/ssec_dm_gaia_source.html#gaia_source-random_index)) to download the first couple of million entries. This is different from queries targeted at different problems, eg. looking for entries within a specific radius of an object of interest, or downloading specific fields of interest, or using subsamples cross-matched with other observations.

The database can be found [at the gaia archive website](https://gea.esac.esa.int/archive/), and documentation about the various fields can be found [here](http://gea.esac.esa.int/archive/documentation/GDR2/).

The specific queries I use are:

    SELECT TOP 1000000 * FROM gaiadr2.gaia_source ORDER BY random_index

and for the next million entries:

    select TOP 1000000 * FROM gaiadr2.gaia_source WHERE random_index >= 1000000 ORDER BY random_index

and so on.

These files can also be found at `/Users/jfwu/projects/gaia-dr2/data` on gradserv.

## Initial visualization:

Imported the data from the first million or so objects into a pandas DataFrame, started making basic plots to see what the minimum size of an analysis sample ought to be.

Note: `matplotlib` has a mollweide projection option that can be triggered using

    ax = fig.add_subplot(111, projection = 'mollweide')

# Project Ideas

1. Streams (solar neighbourhood or galactic)
    - identify them in phase space (which phase space variables do we use?)

2. High velocity Stars
    - clusters?

3. Globular clusters
    - multiple populations, dynamics consistent with intermediate mass BHs

4. 2 or 3 star systems
    - fraction, distribution with stellar mass (how do we get those? from colors, temp?)

5. Variable objects
    - look for databases [here](http://cdn.gea.esac.esa.int/Gaia/gdr2/).
