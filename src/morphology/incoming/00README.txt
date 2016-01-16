WHAT IS THIS???!!!

The intended use of this directory is to hold (in svn) files and documents of
incoming lexical resources to be transformed more or less manually to lexc (or
xml) files (the lexc or xml files are the real source files used in the build
process).

That is, store here any files used as a source for lexicalisation.

NB! Unless your language is a closed-source language, everything stored here
will be freely accessible to the whole world! This is intentional and in
accordance with our open-source philosophy, but may not be compatible with the
license of the files to be used for lexicalisation. If so, contact the
administrators to discuss alternative solutions compatible with the lexical
resource's license.


!! 2016-01-15
Testing for coverage of apertium needs:
!! deu-swe
!! (1) update missingDeu2Swe.regex
cat src/morphology/incoming/apertium-deu-swe.deu-swe.dix |grep 'n="'|grep '<e' | perl -pe 's/\ *\<e\>\ *\<p\>\<l\>([^<]*)\<[^\n]*/$1/g; '|hudeu|grep '+?'|gawk '{print $1}' |perl -pe 's/^([^\n]*)/\>$1\</g;' > src/morphology/incoming/missingDeu2Swe.regex

!! (2) update MissingDeu2Swe_01.xml
cat src/morphology/incoming/apertium-deu-swe.deu-swe.dix | grep -f src/morphology/incoming/missingDeu2Swe.regex > src/morphology/incoming/MissingDeu2Swe_01.xml

!! (3) update MissingDeu2Swe_01.xml.lexc
cat src/morphology/incoming/MissingDeu2Swe_01.xml |perl -pe 's/\<e\>\ *\<p\>\<l\>([^<]*)\<s\ n\=\"([^"]*)\"\/\>\<s\ n\=\"([^"]*)\"\/\>\<\/l\>[^\n]*/$1:$1\ __$2_$3\ \;/g; s/\<e\>\ *\<p\>\<l\>([^<]*)\<s\ n\=\"([^"]*)\"\/\>\<\/l\>[^\n]*/$1:$1\ __$2\ \;/g; '|sort|uniq > src/morphology/incoming/MissingDeu2Swe_01.xml.lexc
