valadoc = find_program ('valadoc', required: false)
if valadoc.found()
	gtkdoc_outdir = CAMEL_CASE_NAME+'-'+API_VERSION
	docsdir = join_paths (get_option ('datadir'), 'devhelp','books')

	custom_target ('libgcalc_valadocs',
			input : gcalc_sources,
			output : CAMEL_CASE_NAME+'-'+API_VERSION,
			command : [valadoc,
				'--doclet=devhelp',
				'--force',
				'--fatal-warnings',
				'--package-name='+CAMEL_CASE_NAME+'-'+API_VERSION,
				'--package-version='+meson.project_version(),
				'--vapidir='+gcalc_sources_dir,
				'--vapidir='+gcalc_build_dir,
				'--pkg=glib-2.0',
				'--pkg=gio-2.0',
				'--pkg=gee-0.8',
				'--vapidir='+vapis_dir,
				'--pkg=mpc',
				'--pkg=mpfr',
				'--pkg=mpfrg',
				'--directory=@OUTDIR@',
				'@INPUT@'
				],
			install : true,
			install_dir : docsdir,
			depends: libgcalc
			)
endif