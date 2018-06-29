# MoWSC
Multi-objective Workflow Scheduling in Cloud (rewritten of Hookie)
# Installation Procedure
  sudo -s
  add-apt-repository ppa:couchdb/stable
  apt update
  git clone https://github.com/salehsedghpour/MoWSC
  apt-get install build-essential cmake clang cabal-install python-pip software-properties-common couchdb
  cd MoWSC/c_src
  cmake .
  make
  cabal update
  cabal install HandsomeSoup MonadRandom aeson cmdargs
  cabal install hxt hxt-tagsoup mersenne-random-pure64 unordered-containers vector xorshift
  cd
  git clone https://github.com/salehsedghpour/lcs
  cd lcs
  cabal install lcs.cabal
  cd ~/MoWSC/
  ./Setup.lhs configure --user --extra-include-dirs=~/MoWSC/c_src/ --extra-lib-dirs=~/MoWSC/c_src/
  ./Setup.lhs build
  ./Setup.lhs install
  pip install couchdb gevent matplotlib
  # edit the file in /etc/couchdb/local.ini
  [query_servers]
  python = /home/ubuntu/MoWSC/analysis/query.py
  service couchdb restart
  curl -X PUT http://127.0.0.1:5984/hookie-exp-test





