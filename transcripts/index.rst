.. Speech-to-text reports from DjangoCon Europe 2015 master file, created by
   sphinx-quickstart on Sat Jun  6 09:11:53 2015.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

===================================
DjangoCon Europe 2015 - transcripts
===================================

See the `Git repository <https://github.com/evildmp/DjangoConEuropeTranscripts>`_.


Contents
========

.. toctree::
   :maxdepth: 2

   open_day/index

DjangoCon Europe 2015 was supported by two text-to-speech reporters, Hilary Maclean and Sheryll
Holley.

We have been provided with a transcript of their output (so far, covering day one, the open day).

We need to tidy this up, make corrections, fill in gaps, and publish it so that it is a useful
resource and a near-complete record of proceedings.

AOTV will soon be publishing the video recordings they made of talks, and together those videos,
presenters' slides and these transcripts will be an invaluable resource.

There's a lot of work to do, but if each speaker takes a little time to submit a pull request with
amendments for their own talk, the bulk of the work will be concluded very swiftly.

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


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

