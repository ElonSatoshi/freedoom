# textgen outputs these files which are included in the built WADs
# as lumps.
TEXTGEN_GRAPHIC_LUMPS = \
  m_detail.png m_disopt.png m_disp.png   m_endgam.png m_epi1.png   \
  m_epi2.png   m_epi3.png   m_epi4.png   m_episod.png m_gdhigh.png \
  m_gdlow.png  m_hurt.png   m_jkill.png  m_lgttl.png  m_loadg.png  \
  m_messg.png  m_msens.png  m_msgoff.png m_msgon.png  m_musvol.png \
  m_newg.png   m_ngame.png  m_nmare.png  m_option.png m_optttl.png \
  m_pause.png  m_quitg.png  m_rdthis.png m_rough.png  m_saveg.png  \
  m_scrnsz.png m_sfxvol.png m_sgttl.png  m_skill.png  m_svol.png   \
  m_about.png  m_accel.png  m_auto.png   m_chat.png   m_chatm.png  \
  m_compat.png m_demos.png  m_dmflag.png m_enem.png   m_etcopt.png \
  m_feat.png   m_generl.png m_gset.png   m_horsen.png m_hud.png    \
  m_joyset.png m_keybnd.png m_ldsv.png   m_loksen.png m_menus.png  \
  m_mess.png   m_mouse.png  m_multi.png  m_player.png m_serial.png \
  m_setup.png  m_sound.png  m_stat.png   m_status.png m_tcpip.png  \
  m_versen.png m_video.png  m_wad.png    m_wadopt.png m_weap.png   \
  prboom.png   t_phase1.png t_phase2.png                           \
  m_ultra.png  wibp1.png    wibp2.png    wibp3.png    wibp4.png    \
  wicolon.png  wienter.png  wif.png      wifrgs.png   wipcnt.png   \
  wiminus.png  wimstar.png  wimstt.png   wiostf.png   wiosti.png   \
  wiostk.png   wiosts.png   wiscrt2.png  wisucks.png  witime.png   \
  wip1.png     wip2.png     wip3.png     wip4.png     wipar.png    \
  winum0.png   winum1.png   winum2.png   winum3.png   winum4.png   \
  winum5.png   winum6.png   winum7.png   winum8.png   winum9.png   \
  dmwilv00.png dmwilv01.png dmwilv02.png dmwilv03.png dmwilv04.png \
  dmwilv05.png dmwilv06.png dmwilv07.png dmwilv08.png dmwilv09.png \
  dmwilv10.png dmwilv11.png dmwilv12.png dmwilv13.png dmwilv14.png \
  dmwilv15.png dmwilv16.png dmwilv17.png dmwilv18.png dmwilv19.png \
  dmwilv20.png dmwilv21.png dmwilv22.png dmwilv23.png dmwilv24.png \
  dmwilv25.png dmwilv26.png dmwilv27.png dmwilv28.png dmwilv29.png \
  dmwilv30.png dmwilv31.png                                        \
  cwilv00.png  cwilv01.png  cwilv02.png  cwilv03.png  cwilv04.png  \
  cwilv05.png  cwilv06.png  cwilv07.png  cwilv08.png  cwilv09.png  \
  cwilv10.png  cwilv11.png  cwilv12.png  cwilv13.png  cwilv14.png  \
  cwilv15.png  cwilv16.png  cwilv17.png  cwilv18.png  cwilv19.png  \
  cwilv20.png  cwilv21.png  cwilv22.png  cwilv23.png  cwilv24.png  \
  cwilv25.png  cwilv26.png  cwilv27.png  cwilv28.png  cwilv29.png  \
  cwilv30.png  cwilv31.png                                         \
  wilv00.png   wilv01.png   wilv02.png   wilv03.png   wilv04.png   \
  wilv05.png   wilv06.png   wilv07.png   wilv08.png   wilv10.png   \
  wilv11.png   wilv12.png   wilv13.png   wilv14.png   wilv15.png   \
  wilv16.png   wilv17.png   wilv18.png   wilv20.png   wilv21.png   \
  wilv22.png   wilv23.png   wilv24.png   wilv25.png   wilv26.png   \
  wilv27.png   wilv28.png   wilv30.png   wilv31.png   wilv32.png   \
  wilv33.png   wilv34.png   wilv35.png   wilv36.png   wilv37.png   \
  wilv38.png

# The full set of graphics outputted by textgen includes a couple of
# extra files that are just intermediates, and are not lumps to be
# incuded in the WADs:
TEXTGEN_GRAPHICS = $(TEXTGEN_GRAPHIC_LUMPS)                                \
  helpttl.png  freettl.png

all: graphics.stamp help.png credit.png wikilrs.png wivctms.png

# textgen creates multiple outputs, which is awkward to express in
# make. Use a witness file (graphics.stamp) as suggested in the
# automake manual: "Handling Tools that Produce Many Outputs"

graphics.stamp: textgen.mk $(TEXTGEN_GRAPHICS)
	cp $(TEXTGEN_GRAPHIC_LUMPS) ../
	@touch $@

# Construct a file of Make directives for each text graphic.
# Each graphic depends on the directives file, so we tell textgen
# what its name is, as a command line parameter. The directives
# file depends on textgen's input (config, font, dehacked).

textgen.mk: config.py fontchars ../../lumps/dehacked.lmp
	./textgen $@ > $@

# Then, include the file of Make directives constructed above.

include textgen.mk

# Generate transparent image containing text for the HELP screen:
helptext.png: helpttl.png
	python smtextgen helptext.png 320x200        \
	   150,5   "file:helpttl.png"                \
	   10,25   "Weapons"                         \
	   80,25   "file:../../sprites/shota0.png"   \
	   150,25  "file:../../sprites/sgn2a0.png"   \
	   210,20  "file:../../sprites/mguna0.png"   \
	   10,40   "file:../../sprites/launa0.png"   \
	   80,40   "file:../../sprites/plasa0.png"   \
	   150,40  "file:../../sprites/bfuga0.png"   \
	   240,40  "file:../../sprites/csawa0.png"   \
	   10,67   "Ammo"                            \
	   53,67   "file:../../sprites/clipa0.png"   \
	   68,62   "file:../../sprites/ammoa0.png"   \
	   110,67  "Shells"                          \
	   160,67  "file:../../sprites/shela0.png"   \
	   180,62  "file:../../sprites/sboxa0.png"   \
	   220,67  "Backpack"                        \
	   290,55  "file:../../sprites/bpaka0.png"   \
	   10,90   "Missiles"                        \
	   76,78   "file:../../sprites/rocka0.png"   \
	   95,82   "file:../../sprites/broka0.png"   \
	   170,90  "Energy"                          \
	   220,90  "file:../../sprites/cella0.png"   \
	   240,81  "file:../../sprites/celpa0.png"   \
	   10,115  "Health"                          \
	   63,113  "file:../../sprites/bon1a0.png"   \
	   78,112  "file:../../sprites/stima0.png"   \
	   96,107  "file:../../sprites/media0.png"   \
	   128,107 "file:../../sprites/pstra0.png"   \
	   170,115 "Armor"                           \
	   220,113 "file:../../sprites/bon2a0.png"   \
	   240,105 "file:../../sprites/arm1b0.png"   \
	   280,105 "file:../../sprites/arm2b0.png"   \
	   145,140 "Map"                             \
	   175,130 "file:../../sprites/pmapa0.png"   \
	   10,140  "Overdrive"                       \
	   84,132  "file:../../sprites/soula0.png"   \
	   110,132 "file:../../sprites/megaa0.png"   \
	   10,163  "Night vis."                      \
	   80,160  "file:../../sprites/pvisa0.png"   \
	   10,182  "Stealth"                         \
	   67,172  "file:../../sprites/pinsa0.png"   \
	   115,182 "Invuln."                         \
	   170,174 "file:../../sprites/pinva0.png"   \
	   255,182 "Keys"                            \
	   246,142 "file:../../sprites/rkeya0.png"   \
	   261,142 "file:../../sprites/ykeya0.png"   \
	   276,142 "file:../../sprites/bkeya0.png"   \
	   246,162 "file:../../sprites/rskua0.png"   \
	   261,162 "file:../../sprites/yskua0.png"   \
	   276,162 "file:../../sprites/bskua0.png"   \
	   130,163 "Hazard suit"                     \
	   215,142 "file:../../sprites/suita0.png"

# Make background transparent so it can be overlayed.
helptext2.png : helptext.png
	convert helptext.png -transparent '#00ffff' helptext2.png

# Background for the help screen is a color shifted version of INTERPIC:
helpbg.png: ../interpic.png
	convert ../interpic.png -fill '#5599ff' -tint 100 helpbg.png

# Draw the overlay with text and sprites onto the background to get the
# HELP screen:
help.png: helpbg.png helptext2.png
	convert helpbg.png                              \
	    -draw 'image over 0,0 0,0 helptext2.png'     \
	    help.png
	cp $@ ../

credtext.png: freettl.png credit.txt
	python smtextgen credtext.png 320x200        \
	   120,5  "file:freettl.png"                \
	   10,30  "include:credit.txt"

credtext2.png: credtext.png
	convert credtext.png -transparent '#00ffff' credtext2.png

credit.png: helpbg.png credtext2.png
	convert helpbg.png                             \
	    -draw 'image over 0,0 0,0 credtext2.png'   \
	    credit.png
	cp $@ ../

wikilrs_horiz.png:
	python smtextgen $@ 49x7 \
	    0,0  killers

wikilrs.png: wikilrs_horiz.png
	convert wikilrs_horiz.png -rotate 270 $@
	cp $@ ../

wivctms.png:
	python smtextgen $@ 54x7 \
	    0,0  victims
	cp $@ ../

clean:
	rm -f $(TEXTGEN_GRAPHICS) helpbg.png help.png helptext.png	\
	    helptext2.png graphics.stamp textgen.mk *.pyc credtext.png	\
	    credtext2.png credit.png dmwilv*.png wikilrs.png		\
	    wivctms.png wikilrs_horiz.png ../credit.png ../help.png	\
	    ../wikilrs.png ../wivctms.png
	for graphic in $(TEXTGEN_GRAPHICS); do rm -f ../$$graphic; done
	rm -fr __pycache__
