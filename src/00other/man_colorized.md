```bash
man () {
LESS_TERMCAP_mb=$'\e'"[1;31m" \
LESS_TERMCAP_md=$'\e'"[1;31m" \
LESS_TERMCAP_me=$'\e'"[0m" \
LESS_TERMCAP_se=$'\e'"[0m" \
LESS_TERMCAP_so=$'\e'"[1;44;33m" \
LESS_TERMCAP_ue=$'\e'"[0m" \
LESS_TERMCAP_us=$'\e'"[1;32m" \
command man "$@"
}
```

- http://boredzo.org/blog/archives/2016-08-15/colorized-man-pages-understood-and-customized#comment-822111
- https://www.reddit.com/r/programming/comments/4xyvoe/colorized_man_pages/
