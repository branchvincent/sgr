# TODO

  * Err on checkout if there are pending changes?
  * checkout slowness: investigate
    * pks? delete statements? insert statements?
    * make a quick script to insert N rows into the table and do come commits/explains
  * Somehow (?) record sgfiles in the snap_tree (?) as well (multiple ways to materialize a given image).
    * Is it an issue that an image can now have several parents of different types? Its commit tree parent,
      the previous SQL statement (+ source images) in an sgfile that made it and a link to the whole sgfile as well as
      the original source images.
    * somehow add the sources to the commit message as well?
    * maybe parse the query (not just from sgfile) to see which mountpoints it touches (both read and write) in order
      to know when to invalidate and which actual mountpoint to commit.
    * image hashes are actually globally unique. maybe we just replace the schema qualifiers with them somehow? is it
      sufficient to just have the image hashes there and then do a search across the driver for which mountpoint
      it's actually on?
  * Record schema changes in the DIFF table
  * Figure out a better diff format for both the actual table and displaying it from sg diff
  * Object location indirection: actually test HTTP or replace with a different upload mechanism.
  * Stretch goal: gathering object locations and metadata on pull to see which materialization strategy (copy an image,
    apply some sgfiles or some diffs) is better based on our known remotes.
  * Add logging instead of print statements?