Steps to build the project:

    $ cd ~
    $ git clone git@github.com:matachi/linux-variability-analysis-tools.git
    $ git submodule init
    $ git submodule update
    $ cd linux-variability-analysis-tools
    $ sbt
    > compile
    > package
    > project fm-translation
    > compile
    > package
    > exit

    $ cd ~
    $ git clone git@github.com:matachi/rangeFix.git
    $ cd rangeFix
    $ mkdir lib
    $ cp ../linux-variability-analysis-tools/target/scala-2.11/lvat_2.11-1.0-SNAPSHOT.jar lib
    $ cp ../linux-variability-analysis-tools/fm-translation/target/scala-2.11/fm-translation_2.11-0.5-SNAPSHOT.jar lib
    $ sbt
    > compile

Prerequisites for running rangeFix:

    $ sudo dnf install z3
    $ cd ~
    $ git clone git@github.com:matachi/linux-variability-analysis-tools.extracts.git
    $ git clone --depth 1 --branch linux-2.6.32.y git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git

Run:

    $ cd ~/rangeFix
    $ sbt run-main ca.uwaterloo.gsd.rangeFix.KconfigMain ../linux-variability-analysis-tools.extracts/2.6.32.69.exconfig ../linux-2.6.32.y/.config USB_C67X00_HCD yes

