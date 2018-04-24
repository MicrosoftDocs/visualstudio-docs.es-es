---
title: Carga de trabajo Aplicaciones de ciencia de datos y de análisis
description: La carga de trabajo de Aplicaciones de ciencia de datos y de análisis en Visual Studio reúne los lenguajes Python, R, F# y sus correspondientes distribuciones del entorno en tiempo de ejecución, incluida Anaconda.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs - vs-python
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: dc6d1548a95dd60f2dc05dc1a04953525c4b3b4a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="data-science-and-analytical-applications-workload"></a>Carga de trabajo Aplicaciones de ciencia de datos y de análisis

La carga de trabajo Aplicaciones de ciencia de datos y de análisis de Visual Studio, que puede seleccionar e instalar mediante el instalador de Visual Studio, reúne tres lenguajes y sus correspondientes distribuciones para los entornos de ejecución:

- [R y Microsoft R Client](../rtvs/index.md)
- [Python y Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F# con .NET Framework](/dotnet/fsharp/)

![Carga de trabajo Aplicaciones de ciencia de datos y de análisis en el instalador de Visual Studio](media/data-science-workload.png)

R y Python son dos de los principales lenguajes de scripting que se usan para la ciencia de datos. Ambos lenguajes son fáciles de aprender y son compatibles con un ecosistema completo de paquetes. Estos paquetes se centran en una amplia gama de escenarios, como la adquisición de datos, limpieza, entrenamiento de modelos, implementación y trazado. F# también es un lenguaje de .NET eficaz y esencialmente funcional que resulta adecuado para una amplia variedad de tareas de procesamiento de datos.

<!--Note link on the image because this one is large -->
[![Capturas de pantalla de Visual Studio con R, Python y F#](media/data-science-workload-screens.png)](media/data-science-workload-screens.png)

## <a name="workload-options"></a>Opciones de carga de trabajo

De forma predeterminada, la carga de trabajo instala las opciones siguientes, que se pueden modificar en la sección de resumen de la carga de trabajo en el instalador de Visual Studio:

- Compatibilidad con el idioma F#
- Python:
  - Compatibilidad con el lenguaje Python
  - [Anaconda3 64 bits](https://www.continuum.io) (distribución de Python que incluye completas bibliotecas de ciencia de datos y un intérprete de Python)
  - Compatibilidad web con Python
  - Compatibilidad con plantillas de Cookiecutter
- R:
  - Compatibilidad con el lenguaje R
  - Compatibilidad del entorno de tiempo de ejecución con herramientas de desarrollo de R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (intérprete de R de Microsoft totalmente compatible y admitido por la comunidad, con bibliotecas de ScaleR para cálculos más rápidos en nodos o clústeres concretos. También puede usar cualquier R de [CRAN](https://cran.r-project.org/)).

Aunque F# se incluye con varias cargas de trabajo diferentes y Python cuenta con una carga de trabajo propia, Aplicaciones de ciencia de datos y de análisis es la única carga de trabajo que incluye por ahora R. Sin embargo, también puede instalar R independientemente de la carga de trabajo. En la pestaña **Componentes individuales** del instalador, seleccione las siguientes opciones de R:

- **Actividades de desarrollo > Compatibilidad con el lenguaje R**
- **Actividades de desarrollo > Microsoft R Client**
- **Compiladores, herramientas de compilación y entornos de ejecución > Compatibilidad de runtime con las herramientas de desarrollo de R**

## <a name="sql-server-integration"></a>Integración de SQL Server

SQL Server admite el uso de R y Python para realizar análisis avanzados directamente dentro de SQL Server. La compatibilidad con R se incluye con SQL Server 2016 y versiones posteriores; la compatibilidad con Python está disponible en SQL Server 2017 CTP 2.0 y versiones posteriores.

Ejecutar este código donde ya se encuentran los datos le ofrece una serie de ventajas:

- **Eliminación del movimiento de los datos**: en lugar de mover datos de la base de datos a la aplicación o el modelo, puede crear aplicaciones con R y Python en la base de datos. Esta función elimina las barreras de seguridad, cumplimiento normativo, gobierno, integridad y una gran cantidad de problemas similares relacionados con el movimiento de grandes cantidades de datos. También puede consumir conjuntos de datos que no se puedan ajustar en la memoria de un equipo cliente.

- **Facilidad de implementación**: una vez que tenga preparado el modelo de R o Python, implementarlo en producción se reduce a insertarlo en un script T-SQL. Después, cualquier aplicación cliente SQL escrita en cualquier lenguaje puede aprovechar las ventajas de los modelos y la inteligencia mediante una llamada de procedimiento almacenado. No se necesitan integraciones específicas de R o Python.

- **Rendimiento y escala de nivel empresarial**: puede usar funciones avanzadas de SQL Server como los índices de almacenamiento de tablas y columnas en memoria con las API escalables de alto rendimiento de los paquetes RevoScaleR y RevoScalePy. La eliminación del movimiento de datos también significa que se evitan las restricciones de memoria de cliente a medida que crecen los datos o que se quiere aumentar el rendimiento de la aplicación.

- **Extensibilidad amplia**: puede instalar y ejecutar cualquiera de los paquetes de código abierto de R o Python más recientes en SQL Server para compilar aplicaciones completas de IA y aprendizaje en grandes cantidades de datos en SQL Server. Instalar un paquete en SQL Server es tan sencillo como instalar un paquete en el equipo local.

- **Amplia disponibilidad sin costo adicional**: las integraciones de R y Python están disponibles en todas las ediciones de SQL Server 2017 y versiones posteriores, incluida la edición Express. (La compatibilidad con R está disponible en SQL Server 2016 y versiones posteriores).

Para aprovechar al máximo la integración de SQL Server, use el instalador de Visual Studio para instalar la carga de trabajo **Almacenamiento y procesamiento de datos** con la opción **SQL Server Data Tools**. Esta última opción habilita SQL IntelliSense, el resaltado de sintaxis y la implementación.

![Carga de trabajo de almacenamiento y procesamiento de datos](media/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Opciones de la carga de trabajo de almacenamiento y procesamiento de datos](media/data-storage-workload-options.png)

Para obtener más información:

- [Trabajar con SQL Server y R](../rtvs/sql-server.md)
- [Análisis avanzado con R en SQL Server 2016 en bases de datos (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
- [Python en SQL Server 2017: aprendizaje automático mejorado en bases de datos (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Servicios y SDK adicionales

Además de lo que se incluye directamente en la carga de trabajo Aplicaciones de ciencia de datos y de análisis, el servicio Azure Notebooks y el SDK de Azure para Python también son útiles para la ciencia de datos.

Azure SDK para Python facilita el uso y la administración de los servicios de Microsoft Azure en aplicaciones que se ejecutan en Windows, Mac y Linux. Para más información, vea [SDK de Azure para Python](../python/azure-sdk-for-python.md)

Azure Notebooks (actualmente en versión preliminar) proporciona acceso en línea gratuito a Jupyter Notebooks que se ejecutan en la nube en Microsoft Azure. El servicio incluye blocs de notas de ejemplo de Python, R y F# para que pueda comenzar. Visite [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Capturas de pantalla de Azure Notebooks con el ejemplo Introducción a R](media/data-science-workload-notebooks.png)](media/data-science-workload-notebooks.png)