.. _mpi_file_get_view:


MPI_File_get_view
=================

.. include_body

:ref:`MPI_File_get_view` - Returns the process's view of data in the file.


SYNTAX
------



C Syntax
^^^^^^^^

.. code-block:: c

   #include <mpi.h>

   int MPI_File_get_view(MPI_File fh, MPI_Offset *disp,
   	MPI_Datatype *etype, MPI_Datatype *filetype,
   	char *datarep)


Fortran Syntax (see FORTRAN 77 NOTES)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: fortran

   USE MPI
   ! or the older form: INCLUDE 'mpif.h'
   MPI_FILE_GET_VIEW(FH, DISP, ETYPE,
   	FILETYPE, DATAREP, IERROR)
   	INTEGER	FH, ETYPE, FILETYPE, IERROR
   	CHARACTER*(*)	DATAREP
   	INTEGER(KIND=MPI_OFFSET_KIND)	DISP


Fortran 2008 Syntax
^^^^^^^^^^^^^^^^^^^

.. code-block:: fortran

   USE mpi_f08
   MPI_File_get_view(fh, disp, etype, filetype, datarep, ierror)
   	TYPE(MPI_File), INTENT(IN) :: fh
   	INTEGER(KIND=MPI_OFFSET_KIND), INTENT(OUT) :: disp
   	TYPE(MPI_Datatype), INTENT(OUT) :: etype, filetype
   	CHARACTER(LEN=*), INTENT(OUT) :: datarep
   	INTEGER, OPTIONAL, INTENT(OUT) :: ierror


INPUT PARAMETER
---------------
* ``fh``: File handle (handle).

OUTPUT PARAMETERS
-----------------
* ``disp``: Displacement (integer).
* ``etype``: Elementary data type (handle).
* ``filetype``: File type (handle). See Restrictions, below.
* ``datarep``: Data representation (string).
* ``ierror``: Fortran only: Error status (integer).

DESCRIPTION
-----------

The :ref:`MPI_File_get_view` routine returns the process's view of the data in
the file. The current values of the displacement, etype, and filetype
are returned in *disp,* *etype,* and *filetype,* respectively.

The :ref:`MPI_File_get_view` interface allows the user to pass a
data-representation string via the *datarep* argument.


FORTRAN 77 NOTES
----------------

The MPI standard prescribes portable Fortran syntax for the *DISP*
argument only for Fortran 90. FORTRAN 77 users may use the non-portable
syntax.

.. code-block:: fortran

        INTEGER*MPI_OFFSET_KIND DISP

where ``MPI_OFFSET_KIND`` is a constant defined in ``mpif.h`` and gives the
length of the declared integer in bytes.


ERRORS
------

.. include:: ./ERRORS.rst
