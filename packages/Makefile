packagedirs = adobe-flashplugin/ adobe-pepperflashplugin/ adobe-reader/ \
              cmaptools/ dropbox/ geogebra/ google-chrome/ google-earth/ \
              marvinsketch/ msttcorefonts/ oracle-java/ skype/ \
              spotify-client/ vstloggerpro/
packagefiles = $(packagedirs:%/=%.tar.gz)

all: $(packagefiles) puavo-pkg-installers-bundle.tar

puavo-pkg-installers-bundle.tar: $(packagefiles)
	tar cf "$@" $^

# Do not use tar with -z, instead use "gzip -n" so that tar-archives are
# deterministically created and thus different only when their contents have
# changed (we use tar-archive contents as installer versions).
%.tar.gz: %/ %/*
	tar --mtime='2000-01-01 00:00:00 +00:00' -c -f - $< | gzip -n > "$@"

clean:
	rm -rf $(packagefiles) puavo-pkg-installers-bundle.tar

.PHONY: all clean
