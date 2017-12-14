# <a name="view-recent-job-performance-and-details"></a>Ver el rendimiento y los detalles de trabajos recientes
Una vez que se envían los trabajos, puede ver la lista de trabajos para ver su estado, duración y mucho más.

1. En el **Explorador de servidores** expanda el contexto de ejecución específico 
1. Haga doble clic en **Trabajos**
1. Verá la lista de trabajos enviados a ese contexto de ejecución. 
1. Seleccione un **Trabajo** determinado en la lista para ver los detalles

![Supervisar trabajos](media\job-details\monitor-jobs.png)

> El historial de los trabajos enviados a las máquinas virtuales de Linux se almacena en el directorio /tmp de la máquina virtual. Por tanto, cada vez que se reinicia, se borra el historial de trabajos. Para un registro permanente del historial de trabajos, configure la máquina virtual como un contexto de ejecución en Azure Machine Learning y después envíe el trabajo a Azure Machine Learning (y seleccione la máquina virtual como el contexto de ejecución)