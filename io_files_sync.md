## Google drive

## Install 

    https://github.com/astrada/google-drive-ocamlfuse

## init

    google-drive-ocamlfuse

## mount/sync

    google-drive-ocamlfuse -verbose -f {folder}

## Unmount

    fusermount -u {folder}

## rsync from to

    rsync -zarv --no-links --include='*.ipynb' --include='*.py' --include='*/' --exclude="*" from/  to/
