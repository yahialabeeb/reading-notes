# matplotlib 
* matplotlib is probably the single most used Python package for 2D-graphics. 

## IPython
* IPython is an enhanced interactive Python shell that has lots of interesting features including named inputs and outputs, access to shell commands, improved debugging and much more. It allows interactive matplotlib sessions that have Matlab/Mathematica-like functionality.

## pyplot
* pyplot provides a convenient interface to the matplotlib object-oriented plotting library. 

## Instantiating defaults
 ### Changing colors and line widths
 >color="blue", linewidth=2.5, linestyle="-"
 ### Setting limits
 >plt.xlim(X.min()*1.1, X.max()*1.1)
 ### Setting ticks
 >plt.yticks([-1, 0, +1])

 ### Setting tick labels
 >plt.yticks([-1, 0, +1],[r'$-1$', r'$0$', r'$+1$'])
 ### Moving spines
 * Spines are the lines connecting the axis tick marks and noting the boundaries of the data area.
 ```python 
 ax.spines['right'].set_color('none')
 ax.spines['top'].set_color('none')
 ax.xaxis.set_ticks_position('bottom') 
 ax.spines['bottom'].set_position(('data',0)) 
 ax.yaxis.set_ticks_position('left')
 ax.spines['left'].set_position(('data',0))
 ```

 ### Adding a legend
 > plt.legend(loc='upper left', frameon=False)
 ### Annotate some points
 ``` python 
 plt.annotate(r'$\sin(\frac{2\pi}{3})=\frac{\sqrt{3}}{2}$',
 xy=(t, np.sin(t)), xycoords='data',
 xytext=(+10, +30), textcoords='offset points', fontsize=16,
 arrowprops=dict(arrowstyle="->", connectionstyle="arc3,rad=.2"))
 ```
 ### Other Types of Plots

1. plot 
1. scatter 
1. bar 
1. contour 
1. imshow 
1. quiver 
1. pie 
1. grid 
1. multiplot 
1. polar 
1. plot3d 
1. text
1. Regular Plots