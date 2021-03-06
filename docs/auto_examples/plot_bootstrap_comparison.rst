.. only:: html

    .. note::
        :class: sphx-glr-download-link-note

        Click :ref:`here <sphx_glr_download_auto_examples_plot_bootstrap_comparison.py>`     to download the full example code
    .. rst-class:: sphx-glr-example-title

    .. _sphx_glr_auto_examples_plot_bootstrap_comparison.py:


========================
ODP Bootstrap Comparison
========================

This example demonstrates how you can drop the outlier link ratios from the
BootstrapODPSample to reduce reserve variability estimates.




.. image:: /auto_examples/images/sphx_glr_plot_bootstrap_comparison_001.png
    :alt: plot bootstrap comparison
    :class: sphx-glr-single-img


.. rst-class:: sphx-glr-script-out

 Out:

 .. code-block:: none

    c:\users\jboga\onedrive\documents\github\chainladder-python\chainladder\development\base.py:170: UserWarning: drop_high and drop_low cannot be computed when less than three LDFs are present. Ignoring exclusions in some cases.
      warnings.warn('drop_high and drop_low cannot be computed '
    c:\users\jboga\onedrive\documents\github\chainladder-python\chainladder\utils\weighted_regression.py:62: RuntimeWarning: invalid value encountered in sqrt
      residual = (y-fitted_value)*xp.sqrt(w)
    c:\users\jboga\onedrive\documents\github\chainladder-python\chainladder\development\base.py:264: RuntimeWarning: invalid value encountered in sqrt
      xp.swapaxes(xp.sqrt(x**(2-val))[..., 0:1, :], -1, -2))

    [Text(0.5,0,'Ultimate')]





|


.. code-block:: default

    import chainladder as cl

    # Load triangle
    triangle = cl.load_sample('raa')

    # Use bootstrap sampler to get resampled triangles
    s1 = cl.BootstrapODPSample(
        n_sims=5000, random_state=42).fit(triangle).resampled_triangles_

    ## Alternatively use fit_transform() to access resampled triangles dropping
    #  outlier link-ratios from resampler
    s2 = cl.BootstrapODPSample(
        drop_high=True, drop_low=True,
        n_sims=5000, random_state=42).fit_transform(triangle)

    # Summarize results of first model
    results = cl.Chainladder().fit(s1).ibnr_.sum('origin').rename('columns', ['Original'])
    # Add another column to triangle with second set of results.
    results['Dropped'] = cl.Chainladder().fit(s2).ibnr_.sum('origin')

    # Plot both IBNR distributions
    results.to_frame().plot(kind='hist', bins=50, alpha=0.5, grid=True).set(
        xlabel='Ultimate')


.. rst-class:: sphx-glr-timing

   **Total running time of the script:** ( 0 minutes  4.983 seconds)


.. _sphx_glr_download_auto_examples_plot_bootstrap_comparison.py:


.. only :: html

 .. container:: sphx-glr-footer
    :class: sphx-glr-footer-example



  .. container:: sphx-glr-download sphx-glr-download-python

     :download:`Download Python source code: plot_bootstrap_comparison.py <plot_bootstrap_comparison.py>`



  .. container:: sphx-glr-download sphx-glr-download-jupyter

     :download:`Download Jupyter notebook: plot_bootstrap_comparison.ipynb <plot_bootstrap_comparison.ipynb>`


.. only:: html

 .. rst-class:: sphx-glr-signature

    `Gallery generated by Sphinx-Gallery <https://sphinx-gallery.github.io>`_
