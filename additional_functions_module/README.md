# Python Module

This is a *Python module* with useful functions.


* <code>print_all_dataframe (rows, columns):</code> sets the number of rows and columns to be printed when displaying a <code>Pandas DataFrame</code>.

      :param rows: Number of rows to display.
      :param columns: Number of columns to display.

* <code>display_side_by_side (*args, titles=cycle([''])):</code> prints multiple <code>Pandas DataFrames</code> in the same line.

      :param args: Pandas DataFrames to be printed.
      :param titles: titles to be printed above the <code>Pandas DataFrames</code> (optional).
  
* <code>sdescribe (df, column, decimals):</code> calculates the descriptive statistics of a numeric variable in a <code>Pandas DataFrame</code>. Note that *kurtosis* follows *Pearson's definition* (normal ==> 3.0).
  
      :param df: a Pandas DataFrame containing the data.
      :param column: the name of the column containing the quantitative variable.
      :param decimals: the number of decimals to be printed.
      :return: descriptive statistics of the variable, including count, mean, standard deviation (std), minimum (min), P25%, P50%, P75%, maximum (max), skewness (skew), and kurtosis (kurt).

 * <code>freqtab (df, column, decimals):</code> calculates the descriptive statistics of a qualitative variable in a <code>Pandas DataFrame</code>.
      :param df: a Pandas DataFrame containing the data.
      :param column: the name of the column containing the qualitative variable.
      :param decimals: the number of decimals to print.
      :return: frequency table of a qualitative variable, including total count and percentage.

* <code>plot(df, x_axis, axis, kind, hue=None):</code> plots barplots and boxplots of qualitative variables in a <code>Pandas DataFrame</code> including <code>NAs.</code>

      :param df: a Pandas DataFrame containing the data.
      :param x_axis: the name of the column containing the variable to plot.
      :param axis: axis of a matplotlib subplots figure where the figure is going to be plotted.
      :param kind: the kind of plot, including "bars" or "box".
      :param hue: (default = None) adds an additional dimension to the plot by splitting the distribution based on a variable.   
      :return: the plot.

------------------------------------------------
