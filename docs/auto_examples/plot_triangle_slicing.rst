.. only:: html

    .. note::
        :class: sphx-glr-download-link-note

        Click :ref:`here <sphx_glr_download_auto_examples_plot_triangle_slicing.py>`     to download the full example code
    .. rst-class:: sphx-glr-example-title

    .. _sphx_glr_auto_examples_plot_triangle_slicing.py:


================================
Pandas-style slicing of Triangle
================================

This example demonstrates the familiarity of the pandas API applied to a
:class:`Triangle` instance.




.. image:: /auto_examples/images/sphx_glr_plot_triangle_slicing_001.png
    :alt: Medical Malpractice Link Ratios
    :class: sphx-glr-single-img






.. code-block:: default

    import chainladder as cl

    # The base Triangle Class:
    cl.Triangle

    # Load data
    clrd = cl.load_sample('clrd')
    # pandas-style Aggregations
    clrd = clrd.groupby('LOB').sum()
    # pandas-style value/column slicing
    clrd = clrd['CumPaidLoss']
    # pandas loc-style index slicing
    clrd = clrd.loc['medmal']

    # Plot
    g = clrd.link_ratio.plot(
        marker='o', grid=True,
        title='Medical Malpractice Link Ratios').set(
        ylabel='Link Ratio', xlabel='Accident Year');


.. rst-class:: sphx-glr-timing

   **Total running time of the script:** ( 0 minutes  1.131 seconds)


.. _sphx_glr_download_auto_examples_plot_triangle_slicing.py:


.. only :: html

 .. container:: sphx-glr-footer
    :class: sphx-glr-footer-example



  .. container:: sphx-glr-download sphx-glr-download-python

     :download:`Download Python source code: plot_triangle_slicing.py <plot_triangle_slicing.py>`



  .. container:: sphx-glr-download sphx-glr-download-jupyter

     :download:`Download Jupyter notebook: plot_triangle_slicing.ipynb <plot_triangle_slicing.ipynb>`


.. only:: html

 .. rst-class:: sphx-glr-signature

    `Gallery generated by Sphinx-Gallery <https://sphinx-gallery.github.io>`_
