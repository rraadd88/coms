# Start the IPython kernel on the server with the following options:

ipython notebook --no-browser --port=7000

# Set up a ssh connection to the server on your local machine with the following options:

ssh -N -f -L localhost:7000:localhost:7000 name@192.168.XX.XX

# Now you can access the notebook by directing your browser to:

localhost:7000

# You can check the host from the notebook by typing:

import socket
socket.gethostname()


