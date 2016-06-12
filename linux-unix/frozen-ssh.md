# frozen ssh

No need to `Ctrl+B X` inside tmux on frozen ssh because of crappy network connection

Simply press:
  - [ENTER] (Return key)
  - ~ (Tilde)
  - . (Period)

This will send escape sequence to local ssh client and terminate the connection. Handy!

Credits: http://blog.infertux.com/2012/12/20/properly-close-a-frozen-ssh-session/
