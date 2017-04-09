#############################################################################
#
#  XFOIL
#
#  Copyright (C) 2000 Mark Drela
#
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this program; if not, write to the Free Software
#  Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#
#############################################################################

set(XFOIL_SRCS xfoil.f xpanel.f xoper.f xtcam.f xgdes.f xqdes.f xmdes.f
  CIRCLE.INC xsolve.f xbl.f XBL.INC xblsys.f xpol.f 
  XDES.INC xgeom.f xutils.f aread.f naca.f
  spline.f iopol.f PINDEX.INC sort.f XFOIL.INC
  profil.f userio.f)

add_executable(xfoil ${XFOIL_SRCS})
set_target_properties(xfoil PROPERTIES VERSION ${PROJECT_VERSION})
target_link_libraries(xfoil)

export(TARGETS xfoil FILE "${CMAKE_BINARY_DIR}/xfoil-targets.cmake")

install(TARGETS xfoil EXPORT xfoil-targets DESTINATION ${CMAKE_INSTALL_BINDIR})
install(EXPORT xfoil-targets
  DESTINATION ${CMAKE_INSTALL_DATADIR}/${PROJECT_NAME})

set(XFOIL_COPYING gpl.txt)
install(FILES ${XFOIL_COPYING} DESTINATION ${CMAKE_INSTALL_DOCDIR}
  RENAME COPYING)


