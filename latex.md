- Where should installed packages go?
    The command `kpsewhich -var-value=TEXMFHOME` shows where the TeX engine
    will search for packages (kinda like a `PATH`). `kpsewhich <package>.sty`
    will show what package the TeX engine finds (kinda like `which`). `strace`
    shows that it expects a directory structure like `$(kpsewhich
    -var-value=TEXMFHOME)/tex/<package>`
- Why are quotation marks the wrong way?
    TeX wants quotes written as `\`\`` and `''` for opening and closing
    quotations, respectively.
