# preprocess

This command allows the user to add entries to the internal database. There are two possible modes for the `preprocess` command: `add` and `extend`.

## preprocess --mode add
In case of `add` mode, an entry will be created based on the input files and parameters provided.


Example of usage of mode `add`:

```shell
python preprocessor/cellstar_preprocessor/preprocess.py preprocess --mode add --input-path test-data/preprocessor/sample_volumes/emdb/EMD-1832.map --input-kind map --entry-id emd-1832 --source-db emdb --source-db-id emd-1832 --source-db-name emdb --working-folder temp_working_folder --db-path preprocessor/temp/test_db
```

This command will add an `emd-1832` entry to the internal database, throwing an exception if this entry already exists.


## prepocess --mode extend

Another option is mode `extend` which will extend the entry data with e.g. additional segmentation. For example, initially an `emd-1832` entry may be added to the database using mode `add` (see code listing above). Note that at this point it contains only the volume data as we provided only the electron density map as input.

Then the user may decide to add segmentation data to it. This can be achieved using mode `extend` of `preprocess` command:

```shell
python preprocessor/cellstar_preprocessor/preprocess.py preprocess --mode extend --input-path test-data/preprocessor/sample_segmentations/emdb_sff/emd_1832.hff --input-kind sff --entry-id emd-1832 --source-db emdb --source-db-id emd-1832 --source-db-name emdb --working-folder temp_working_folder --db-path preprocessor/temp/test_db
```

Note that the values of arguments `--entry-id`, `--source-db`, `--source-db-id`, `--source-db-name`, and `--db-path` should be exactly the same as the ones used when the entry was initially created using mode `add`. After using this command, the `emd-1832` entry will have not only volume data, but also lattice segmentation data based on the provided EMDB SFF file.
