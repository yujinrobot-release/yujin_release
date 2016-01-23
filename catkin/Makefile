SHELL := /bin/bash

ifndef SOURCE_BRANCH
  $(info SOURCE_BRANCH undefined, setting to $(TRACK))
  SOURCE_BRANCH=$(TRACK)
endif

help:
	@echo "Valid git targets:"
	@echo "  clone  : clone all source and release repos."
	@echo "  pull   : pull latest from all source and release repos."
	@echo "  push   : push all release repos."
	@echo "  reset  : reset all release repos to HEAD state."
	@echo "  clean  : clear all cloned repos."
	@echo ""
	@echo "Valid bloom targets:"
	@echo "  config : point the release repo at the source repo (one time only)"
	@echo "  bloom  : run a release for the repo."

clone:
	@for i in ${REPOS}; do \
          git clone ${SRC_GIT}/$${i}.git; \
	  cd $${i}; \
	  git checkout -b ${SOURCE_BRANCH} origin/${SOURCE_BRANCH}; \
	  cd ..; \
	  git clone ${REL_GIT}/$${i}-release.git; \
        done


pull:
	@for i in ${REPOS}; do \
          cd ${CURDIR}/$${i}; git pull; \
          cd ${CURDIR}/$${i}-release; git pull; \
        done

push:
	@for i in ${REPOS}; do \
          cd ${CURDIR}/$${i}-release; git push --all; git push --tag; \
	done

reset:
	@for i in ${REPOS}; do \
          cd ${CURDIR}/$${i}-release; git reset --hard HEAD; \
	done

config:
	@for i in ${REPOS}; do \
          cd ${CURDIR}/$${i}-release; git-bloom-config new ${TRACK}; git push --all; git push --tag; \
	done

edit:
	@for i in ${REPOS}; do \
          cd ${CURDIR}/$${i}-release; git-bloom-config edit ${TRACK}; git push --all; git push --tag; \
	done

bloom:
	@for i in ${REPOS}; do \
          bloom-release --track ${TRACK} --rosdistro ${TRACK} $${i}; \
	done

package:
	@for i in ${REPOS}; do \
	  echo "Make sure you checkout the branch first, e.g."; \
	  echo "  git checkout -b debian/ros-${TRACK}-<package-dash-name>_<version>_precise"; \
          cd ${CURDIR}/$${i}-release; git-buildpackage -uc -us  --git-ignore-new --git-upstream-tree=tag; \
	done
	
clean:
	@for i in ${REPOS}; do \
          rm -rf $${i}; \
          rm -rf $${i}-release; \
        done

