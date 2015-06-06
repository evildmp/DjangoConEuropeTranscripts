==========================
DjangoConEuropeTranscripts
==========================

Proceedings from DjangoCon Europe 2015.

`Published on Read the Docs <http://djangoconeuropetranscripts.readthedocs.org>`_.

How we should work
==================

In the root of the GitHub repository:

* ``.docx`` files (such as ``Djangocon 31st May 15 Open Day FINAL.docx``) are the originals
  provided by the STTRs - they should not be edited in any way
* ``raw_transcript.txt`` files (such as ``open_day_raw_transcript.txt``) are plain text versions of
  the above - they should not be edited in any way
* ``working_copy.txt`` files (such as ``open_day_working_copy.txt``) are copies of the above - they
  **can** be edited

When a section of a ``working_copy.txt`` file has been moved to a new location in the transcripts,
it should be removed from the ``working_copy.txt``, so we can see what remains to be transferred.

Structure
=========

Please use this directory/file structure so we can easily link from the published videos on Vimeo
to each transcript:

  * Transcripts

    * ``index.rst``
    * Open Day at Cardiff University

      * ``index.rst``
      * ``daniele_procida_welcome_to_djangocon.rst`` Daniele Procida: Welcome to DjangoCon Europe
        2015
      * ``roger_whitaker_welcome_to_djangocon.rst`` Roger Whitaker: Welcome to Cardiff University
      * ``russell_keith_magee_what_on_earth.rst`` Russell Keith-Magee: What on earth are Python and
        Django?
      * and so on

    * Talks Day One

      * ``index.rst``
      * talk one
      * talk two
      * ... etc

Introductions, questions and thank-yous should be included with each talk file.

Announcements in-between talks probably don't deserve to be kept for the published transcripts,
unless they are important or particularly interesting.
