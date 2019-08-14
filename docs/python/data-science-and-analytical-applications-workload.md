---
title: Carga de trabajo Aplicaciones de ciencia de datos y de análisis
description: Esta carga de trabajo de Visual Studio reúne Python, F# y sus correspondientes distribuciones de tiempo de ejecución, incluida Anaconda. (R también se incluye en Visual Studio 2017 únicamente).
ms.date: 02/28/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 20ebd6def9fcac2336ca13118300737b66142812
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926395"
---
# <a name="install-data-science-support-in-visual-studio"></a>Instalación de la compatibilidad con ciencia de datos en Visual Studio

La carga de trabajo Aplicaciones de ciencia de datos y de análisis, que se selecciona e instala mediante el instalador de Visual Studio, reúne varios lenguajes y sus correspondientes distribuciones de tiempo de ejecución:

::: moniker range="vs-2017"
- [Python y Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F# con .NET Framework](/dotnet/fsharp/)
- [R y Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [F# con .NET Framework](/dotnet/fsharp/)
::: moniker-end

![Carga de trabajo Aplicaciones de ciencia de datos y de análisis en el instalador de Visual Studio](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
R y Python son dos de los principales lenguajes de scripting que se usan para la ciencia de datos. Ambos lenguajes son fáciles de aprender y son compatibles con un ecosistema completo de paquetes. Estos paquetes se centran en una amplia gama de escenarios, como la adquisición de datos, limpieza, entrenamiento de modelos, implementación y trazado. F# también es un lenguaje de .NET eficaz y esencialmente funcional que resulta adecuado para una amplia variedad de tareas de procesamiento de datos.
::: moniker-end

::: moniker range="vs-2019"
Python es un lenguaje de scripting fundamental que se usa para la ciencia de datos. Python es fácil de aprender y es compatible con un ecosistema completo de paquetes. Estos paquetes se centran en una amplia gama de escenarios, como la adquisición de datos, limpieza, entrenamiento de modelos, implementación y trazado. F# también es un lenguaje de .NET eficaz y esencialmente funcional que resulta adecuado para una amplia variedad de tareas de procesamiento de datos. (Para el lenguaje R se recomienda [Azure Notebooks](https://notebooks.azure.com)).
::: moniker-end

<!--Note link on the image because this one is large -->
[![Capturas de pantalla de Visual Studio con R, Python y F#](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Opciones de carga de trabajo

De forma predeterminada, la carga de trabajo instala las opciones siguientes, que se pueden modificar en la sección de resumen de la carga de trabajo en el instalador de Visual Studio:

::: moniker range="vs-2019"
- Compatibilidad con el lenguaje de escritorio F#
- Python:
  - Compatibilidad con el lenguaje Python
  - Compatibilidad web con Python
::: moniker-end

::: moniker range="vs-2017"
- Compatibilidad con el idioma F#
- Python:
  - Compatibilidad con el lenguaje Python
  - [Anaconda3 64 bits](https://www.continuum.io), una distribución de Python que incluye completas bibliotecas de ciencia de datos y un intérprete de Python.
  - Compatibilidad web con Python
  - Compatibilidad con plantillas de Cookiecutter
- R:
  - Compatibilidad con el lenguaje R
  - Compatibilidad del entorno de tiempo de ejecución con herramientas de desarrollo de R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (intérprete de R de Microsoft totalmente compatible y admitido por la comunidad, con bibliotecas de ScaleR para cálculos más rápidos en nodos o clústeres concretos. También puede usar cualquier R de [CRAN](https://cran.r-project.org/)).
::: moniker-end

## <a name="sql-server-integration"></a>Integración de SQL Server

::: moniker range="vs-2017"
SQL Server admite el uso de R y Python para realizar análisis avanzados directamente dentro de SQL Server. La compatibilidad con R se incluye con SQL Server 2016 y versiones posteriores; la compatibilidad con Python está disponible en SQL Server 2017 CTP 2.0 y versiones posteriores.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server admite el uso de Python para realizar análisis avanzados directamente dentro de SQL Server. La compatibilidad con Python está disponible en SQL Server 2017 CTP 2.0 y versiones posteriores.
::: moniker-end

Ejecutar este código donde ya se encuentran los datos le ofrece una serie de ventajas:

- **Eliminación del movimiento de datos**: En lugar de mover datos de la base de datos a la aplicación o el modelo, puede compilar aplicaciones en la base de datos. Esta función elimina las barreras de seguridad, cumplimiento normativo, gobernanza, integridad y una gran cantidad de problemas similares relacionados con el movimiento de grandes cantidades de datos. También puede consumir conjuntos de datos que no se puedan ajustar en la memoria de un equipo cliente.

- **Facilidad de implementación**: Una vez que tenga listo un modelo, implementarlo en producción es tan sencillo como insertarlo en un script T-SQL. Después, cualquier aplicación cliente SQL escrita en cualquier lenguaje puede aprovechar las ventajas de los modelos y la inteligencia mediante una llamada de procedimiento almacenado. No se necesitan integraciones específicas del lenguaje.

- **Rendimiento y escala de nivel empresarial**: Puede usar funciones avanzadas de SQL Server como los índices de almacenamiento de tablas y columnas en memoria con las API escalables de alto rendimiento de los paquetes RevoScale. La eliminación del movimiento de datos también significa que se evitan las restricciones de memoria de cliente a medida que crecen los datos o que se quiere aumentar el rendimiento de la aplicación.

- **Extensibilidad amplia**: Puede instalar y ejecutar cualquiera de los paquetes de código abierto más recientes en SQL Server para compilar aplicaciones completas de IA y aprendizaje en grandes cantidades de datos en SQL Server. Instalar un paquete en SQL Server es tan sencillo como instalar un paquete en el equipo local.

- **Amplia disponibilidad sin costo adicional**: Las integraciones de lenguaje están disponibles en todas las ediciones de SQL Server 2017 y posterior, incluida la edición Express.

Para aprovechar al máximo la integración de SQL Server, use el instalador de Visual Studio para instalar la carga de trabajo **Almacenamiento y procesamiento de datos** con la opción **SQL Server Data Tools**. Esta última opción habilita SQL IntelliSense, el resaltado de sintaxis y la implementación.

![Carga de trabajo de almacenamiento y procesamiento de datos](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Opciones de la carga de trabajo de almacenamiento y procesamiento de datos](media/workload/data-storage-workload-options.png)

Para obtener más información:

::: moniker range="vs-2017"
- [Trabajar con SQL Server y R](../rtvs/integrating-sql-server-with-r.md)
- [Análisis avanzado con R en SQL Server 2016 en bases de datos (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
::: moniker-end
- [Python en SQL Server 2017: aprendizaje automático mejorado en bases de datos (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Servicios y SDK adicionales

Además de lo que se incluye directamente en la carga de trabajo Aplicaciones de ciencia de datos y de análisis, el servicio Azure Notebooks y el SDK de Azure para Python también son útiles para la ciencia de datos.

Azure SDK para Python facilita el uso y la administración de los servicios de Microsoft Azure en aplicaciones que se ejecutan en Windows, Mac y Linux. Para más información, vea [SDK de Azure para Python](../python/azure-sdk-for-python.md).

Azure Notebooks (actualmente en versión preliminar) proporciona acceso en línea gratuito a Jupyter Notebooks que se ejecutan en la nube en Microsoft Azure. El servicio incluye blocs de notas de ejemplo de Python, R y F# para que pueda comenzar. Visite [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Capturas de pantalla de Azure Notebooks con el ejemplo Introducción a R](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
