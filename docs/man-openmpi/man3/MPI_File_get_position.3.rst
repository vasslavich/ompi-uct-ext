.. _mpi_file_get_position:


MPI_File_get_position
=====================

.. include_body

:ref:`MPI_File_get_position` - Returns the current position of the
individual file pointer.


SYNTAX
------



C Syntax
^^^^^^^^

.. code-block:: c

   #include <mpi.h>

   int MPI_File_get_position(MPI_File fh, MPI_Offset *offset)


Fortran Syntax (see FORTRAN 77 NOTES)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: fortran

   USE MPI
   ! or the older form: INCLUDE 'mpif.h'
   MPI_FILE_GET_POSITION(FH, OFFSET, IERROR)
   	INTEGER	FH, IERROR
   	INTEGER(KIND=MPI_OFFSET_KIND)	OFFSET


Fortran 2008 Syntax
^^^^^^^^^^^^^^^^^^^

.. code-block:: fortran

   USE mpi_f08
   MPI_File_get_position(fh, offset, ierror)
   	TYPE(MPI_File), INTENT(IN) :: fh
   	INTEGER(KIND=MPI_OFFSET_KIND), INTENT(OUT) :: offset
   	INTEGER, OPTIONAL, INTENT(OUT) :: ierror


INPUT PARAMETER
---------------
* ``fh``: File handle (handle).

OUTPUT PARAMETERS
-----------------
* ``offset``: Offset of the individual file pointer (integer).
* ``ierror``: Fortran only: Error status (integer).

DESCRIPTION
-----------

:ref:`MPI_File_get_position` returns, in *offset,* the current position of the
individual file pointer in *etype* units relative to the current
displacement and file type.


FORTRAN 77 NOTES
----------------

The MPI standard prescribes portable Fortran syntax for the *OFFSET*
argument only for Fortran 90. Sun FORTRAN 77 users may use the
non-portable syntax

.. code-block:: fortran

        INTEGER*MPI_OFFSET_KIND OFFSET

where ``MPI_ADDRESS_KIND`` is a constant defined in ``mpif.h`` and gives the
length of the declared integer in bytes.


ERRORS
------

.. include:: ./ERRORS.rst
