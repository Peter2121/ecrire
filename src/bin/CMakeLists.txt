LIST(APPEND ECRIRE_CC_SOURCES
   main.c
   cfg.c
   ui/file_related.c
   ui/search_dialog.c
   ui/goto_dialog.c
   ui/settings_dialog.c
   ui/alerts.c
   )

include_directories(
   ${EO_INCLUDE_DIRS}
   ${EINA_INCLUDE_DIRS}
   ${ELEMENTARY_INCLUDE_DIRS}
   ${EDJE_INCLUDE_DIRS}
   ${ECORE_INCLUDE_DIRS}
   ${ECORE_INPUT_INCLUDE_DIRS}
   ${EFREET_INCLUDE_DIRS}
   ${EFREET_MIME_INCLUDE_DIRS}
   ${EVAS_INCLUDE_DIRS}
   ${EET_INCLUDE_DIRS}
   )

IF (Intl_FOUND)
   include_directories(${Intl_INCLUDE_DIRS})
ENDIF (Intl_FOUND)

add_executable(ecrire ${ECRIRE_CC_SOURCES})

IF (Intl_FOUND)
   target_link_libraries(ecrire
      ${EO_LIBRARIES}
      ${EINA_LIBRARIES}
      ${ELEMENTARY_LIBRARIES}
      ${EDJE_LIBRARIES}
      ${ECORE_LIBRARIES}
      ${ECORE_INPUT_LIBRARIES}
      ${EFREET_LIBRARIES}
      ${EFREET_MIME_LIBRARIES}
      ${EVAS_LIBRARIES}
      ${EET_LIBRARIES}
      ${Intl_LIBRARIES}
      )
ELSE (Intl_FOUND)
   target_link_libraries(ecrire
      ${EO_LIBRARIES}
      ${EINA_LIBRARIES}
      ${ELEMENTARY_LIBRARIES}
      ${EDJE_LIBRARIES}
      ${ECORE_LIBRARIES}
      ${ECORE_INPUT_LIBRARIES}
      ${EFREET_LIBRARIES}
      ${EFREET_MIME_LIBRARIES}
      ${EVAS_LIBRARIES}
      ${EET_LIBRARIES}
      )
ENDIF (Intl_FOUND)

install(TARGETS ecrire DESTINATION bin)
