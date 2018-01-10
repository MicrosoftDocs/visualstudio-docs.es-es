---
title: "Carga de trabajo Aplicaciones de ciencia de datos y de análisis en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 09/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
- devlang-python
- devlang-fsharp
ms.tgt_pltfrm: 
ms.topic: landing-page
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: data-science
ms.openlocfilehash: 97debeab6349fefee48d6c550c39c18c3e516b75
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="data-science-and-analytical-applications-workload"></a>Carga de trabajo Aplicaciones de ciencia de datos y de análisis

La carga de trabajo Aplicaciones de ciencia de datos y de análisis de Visual Studio reúne tres lenguajes y sus correspondientes distribuciones de runtime:

- [R y Microsoft R Client](../rtvs/index.md)
- [Python y Anaconda](../python/python-in-visual-studio.md)
- [F# con .NET Framework](https://docs.microsoft.com/dotnet/fsharp/)

![Carga de trabajo Aplicaciones de ciencia de datos y de análisis en el instalador de Visual Studio](media/data-science-workload.png)

R y Python son dos de los principales lenguajes de scripting que se usan para la ciencia de datos. Ambos lenguajes son fáciles de aprender y son compatibles con un ecosistema completo de paquetes. Estos paquetes se centran en una amplia gama de escenarios, como la adquisición de datos, limpieza, entrenamiento de modelos, implementación y trazado. Y F# es un lenguaje de .NET eficaz y esencialmente funcional que resulta adecuado para una amplia variedad de tareas de procesamiento de datos.

<!--Note link on the image because this one is large -->
[![Capturas de pantalla de Visual Studio con R, Python y F#](media/data-science-workload-screens.png)](media/data-science-workload-screens.png)

## <a name="workload-options"></a>Opciones de carga de trabajo

De forma predeterminada, la carga de trabajo instala las opciones siguientes, que se pueden modificar en la sección de resumen de la carga de trabajo en el instalador de Visual Studio:

- Compatibilidad con el idioma F#
- Python:
  - Compatibilidad con el lenguaje Python
  - Compatibilidad web con Python
  - [Anaconda3 64 bits](https://www.continuum.io) (distribución de Python que incluye completas bibliotecas de ciencia de datos y un intérprete de Python)
  - Compatibilidad con plantillas de Cookiecutter
- R:
  - Compatibilidad con el lenguaje R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (intérprete de R de Microsoft totalmente compatible y admitido por la comunidad, con bibliotecas de ScaleR para cálculos más rápidos en nodos o clústeres concretos. También puede usar cualquier R de [CRAN](https://cran.r-project.org/)).
  - Compatibilidad del entorno de tiempo de ejecución con herramientas de desarrollo de R

Aunque F# se incluye con varias cargas de trabajo diferentes y Python cuenta con una carga de trabajo propia, Aplicaciones de ciencia de datos y de análisis es la única carga de trabajo que incluye R en la actualidad. Con independencia de la carga de trabajo, los tres componentes de R también se pueden seleccionar en la pestaña **Componentes individuales** del instalador. Seleccione las opciones **Actividades de desarrollo > Compatibilidad con el lenguaje R**, **Actividades de desarrollo > Microsoft R Client** y **Compiladores, herramientas de compilación y entornos de ejecución > Compatibilidad de runtime con las herramientas de desarrollo de R**.

## <a name="sql-server-integration"></a>Integración de SQL Server

SQL Server admite el uso de R y Python para realizar análisis avanzados directamente dentro de SQL Server. La compatibilidad con R se incluye con SQL Server 2016 y versiones posteriores; la compatibilidad con Python está disponible en SQL Server 2017 CTP 2.0 y versiones posteriores.

Cuando se ejecuta el código donde ya se encuentran los datos, se disfruta de una serie de ventajas:

- **Eliminación del movimiento de los datos**: en lugar de mover datos de la base de datos a la aplicación o el modelo, puede crear aplicaciones con R y Python en la base de datos. Esta función elimina las barreras de seguridad, cumplimiento normativo, gobierno, integridad y una gran cantidad de problemas similares relacionados con el movimiento de grandes cantidades de datos. También permite consumir conjuntos de datos que no se pueden ajustar en la memoria de un equipo cliente.

- **Facilidad de implementación**: una vez listo el modelo de R o Python, implementarlo en producción significa simplemente insertarlo en un script de T-SQL. Después, cualquier aplicación cliente SQL escrita en cualquier lenguaje puede aprovechar las ventajas de los modelos y la inteligencia mediante una llamada de procedimiento almacenado. No se necesitan integraciones específicas de R o Python.

- **Rendimiento y escala de nivel empresarial**: puede usar funciones avanzadas de SQL Server como los índices de almacenamiento de tablas y columnas en memoria con las API escalables de alto rendimiento de los paquetes RevoScaleR y RevoScalePy. La eliminación del movimiento de datos también significa que se evitan las restricciones de memoria de cliente a medida que crecen los datos o que se quiere aumentar el rendimiento de la aplicación.

- **Extensibilidad amplia**: puede instalar y ejecutar cualquiera de los paquetes de código abierto de R o Python más recientes en SQL Server para compilar aplicaciones completas de IA y aprendizaje en grandes cantidades de datos en SQL Server. Instalar un paquete en SQL Server es tan sencillo como instalar un paquete en el equipo local.

- **Amplia disponibilidad sin costo adicional**: las integraciones de R y Python están disponibles en todas las ediciones de SQL Server 2017 y versiones posteriores, incluida la edición Express. (La compatibilidad con R está disponible en SQL Server 2016 y versiones posteriores).

Para aprovechar al máximo la integración de SQL Server, también se debe instalar la carga de trabajo **Almacenamiento y procesamiento de datos** con la opción **SQL Server Data Tools**. Esta opción habilita SQL IntelliSense, el resaltado de sintaxis y la implementación.

![Carga de trabajo de almacenamiento y procesamiento de datos](media/data-storage-workload.png) &nbsp;&nbsp; &nbsp;&nbsp; ![Opciones de la carga de trabajo de almacenamiento y procesamiento de datos](media/data-storage-workload-options.png)

Para obtener más información:

- [Trabajar con SQL Server y R](../rtvs/sql-server.md)
- [Análisis avanzado con R en SQL Server 2016 en bases de datos](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
- [Python en SQL Server 2017: aprendizaje automático mejorado en bases de datos](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Servicios y SDK adicionales

Además de lo que se incluye directamente en la carga de trabajo Aplicaciones de ciencia de datos y de análisis, el servicio Azure Notebooks y el SDK de Azure para Python también son útiles para la ciencia de datos.

Azure SDK para Python facilita el uso y la administración de los servicios de Microsoft Azure en aplicaciones que se ejecutan en Windows, Mac OS X y Linux. Para más información, vea [SDK de Azure para Python](../python/azure-sdk-for-python.md)

Azure Notebooks (actualmente en versión preliminar) proporciona acceso en línea gratuito a Jupyter Notebooks que se ejecutan en la nube en Microsoft Azure. El servicio incluye blocs de notas de ejemplo de Python, R y F# para que pueda comenzar. Visite [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Capturas de pantalla de Azure Notebooks con el ejemplo Introducción a R](media/data-science-workload-notebooks.png)](media/data-science-workload-notebooks.png)