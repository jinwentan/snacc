# file: .../c++-examples/makefile

SUBDIRS		= test-lib simple any snmp

#-------------------------------------------------------------------------------

.PHONY:	implicit_default
implicit_default::
		$(MAKE) subdirs

subdirs::	$(SUBDIRS)
$(SUBDIRS)::
ifeq ($(subtarget)",check)
		echo "Doing "$@" :";
endif
		cd $@ && $(MAKE) $(subtarget)

# the following hack is needed for older make versions (gmake doesn't need it):
init-depend::
		@for dir in $(SUBDIRS); do\
		  test -f $$dir/dependencies || touch $$dir/dependencies;\
		done

.DEFAULT::
		$(MAKE) subdirs subtarget=$@

distfiles::
		echo makefile
		for dir in $(SUBDIRS); do\
		  subfiles=`cd $$dir && $(MAKE) -s $@`;\
		  for file in $$subfiles; do\
		    echo "$$dir/$$file";\
		  done;\
		done

# dummy:
install::
