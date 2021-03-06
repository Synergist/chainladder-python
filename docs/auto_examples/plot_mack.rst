.. only:: html

    .. note::
        :class: sphx-glr-download-link-note

        Click :ref:`here <sphx_glr_download_auto_examples_plot_mack.py>`     to download the full example code
    .. rst-class:: sphx-glr-example-title

    .. _sphx_glr_auto_examples_plot_mack.py:


========================
Mack Chainladder Example
========================

This example demonstrates how you can can use the Mack Chainladder method.



.. image:: /auto_examples/images/sphx_glr_plot_mack_001.png
    :alt: Mack Chainladder Ultimate
    :class: sphx-glr-single-img






.. code-block:: default

    import pandas as pd
    import chainladder as cl

    # Load the data
    data = cl.load_sample('raa')

    # Compute Mack Chainladder ultimates and Std Err using 'simple' average
    mack = cl.MackChainladder()
    dev = cl.Development(average='volume')
    mack.fit(dev.fit_transform(data))

    # Plotting
    plot_data = mack.summary_.to_frame()
    g = plot_data[['Latest', 'IBNR']].plot(
        kind='bar', stacked=True, ylim=(0, None), grid=True,
        yerr=pd.DataFrame({'latest': plot_data['Mack Std Err']*0,
                           'IBNR': plot_data['Mack Std Err']}),
        title='Mack Chainladder Ultimate').set(
        xlabel='Accident Year', ylabel='Loss');


.. rst-class:: sphx-glr-timing

   **Total running time of the script:** ( 0 minutes  0.470 seconds)


.. _sphx_glr_download_auto_examples_plot_mack.py:


.. only :: html

 .. container:: sphx-glr-footer
    :class: sphx-glr-footer-example



  .. container:: sphx-glr-download sphx-glr-download-python

     :download:`Download Python source code: plot_mack.py <plot_mack.py>`



  .. container:: sphx-glr-download sphx-glr-download-jupyter

     :download:`Download Jupyter notebook: plot_mack.ipynb <plot_mack.ipynb>`


.. only:: html

 .. rst-class:: sphx-glr-signature

    `Gallery generated by Sphinx-Gallery <https://sphinx-gallery.github.io>`_
