
<h1 align="center">
    <img src="https://github.com/havakv/pycox/blob/master/figures/logo.svg" alt="pycox" width="200">
</h1>

<p align="center">
    <strong>Time-to-event prediction with PyTorch</strong>
</p>

This repository is a fork of the pycox suite of methods https://github.com/havakv/pycox.

It contains the implementation of the <b>N-MTLR-Rank</b> model, published in https://www.mdpi.com/2227-9059/12/12/2881.

In order to use the model, get the N-MTLR-Rank branch commits, you can then follow the Jupyter notebook for one of the dicrete-time models, for example, N-MTLR: https://nbviewer.org/github/havakv/pycox/blob/master/examples/mtlr.ipynb

Just add the new loss when initializing the model object as follows:
```sh
model = MTLR(net, optimizer, duration_index=labtrans.cuts, loss=NLLMTLRRankLoss(alpha, sigma))
```

N-MTLR-Rank has a loss that is a combination of a N-MTLR loss and a ranking loss. <i>alpha</i> is a parameter that controls the linear combination between the two, and <i>sigma</i> is a parameter used by the ranking loss. <i>alpha = 1</i> gives a loss only containing the negative log-likelihood and <i>alpha = 0</i> give a pure ranking loss.
