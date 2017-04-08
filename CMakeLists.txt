project(patch_cmds)

add_compile_options(
	-nostdinc
)

#add_darling_executable(patch
#	patch/patch.c
#	patch/pch.c
#	patch/inp.c
#	patch/util.c
#	patch/backupfile.c
#	patch/mkpath.c
#)
#target_include_directories(patch PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/patch)
add_darling_executable(diffstat diffstat/diffstat.c)
target_include_directories(diffstat PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/diffstat)
target_compile_definitions(diffstat PRIVATE
	-DHAVE_CONFIG_H
	-D_XOPEN_SOURCE=500
	-D_DARWIN_C_SOURCE
)

install(TARGETS diffstat DESTINATION libexec/darling/usr/bin)

install(FILES
#	patch/patch.1
	diffstat/diffstat.1

	DESTINATION libexec/darling/usr/share/man/man1
)
