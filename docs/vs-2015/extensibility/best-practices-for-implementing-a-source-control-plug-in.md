---
title: Procedimientos recomendados para implementar un complemento de Control de código fuente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 99166c8bf9a76deaa3805bfd8f5ac6db35e5c0a0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995659"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Procedimientos recomendados para implementar un complemento de control de código fuente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los detalles técnicos siguientes pueden ayudarle a implementar un complemento de control de código fuente de forma confiable [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="memory-management-issues"></a>Problemas de administración de memoria  
 En la mayoría de los casos, el entorno de desarrollo integrado (IDE), que es el autor de llamada, se libera y asigna memoria. El complemento de control de origen devuelve cadenas y otros elementos de búferes asignados por el llamador. Las excepciones se indican en las descripciones de funciones específicas donde se producen.  
  
## <a name="arrays-of-file-names"></a>Matrices de los nombres de archivo  
 Cuando se pasa una matriz de archivos, no se pasa como una matriz de nombres de archivo contigua. Se pasa como una matriz de punteros a los nombres de archivo. Por ejemplo, en el [SccGet](../extensibility/sccget-function.md), los nombres de archivo se pasan por el `lpFileNames` parámetro, donde `lpFileNames` es realmente un puntero a un `char **`. `lpFileNames`[0] es un puntero al nombre, `lpFileNames`[1] es un puntero para el nombre de la segunda y así sucesivamente.  
  
## <a name="large-model"></a>Modelo de gran tamaño  
 Todos los punteros son de 32 bits, incluso en sistemas operativos de 16 bits.  
  
## <a name="fully-qualified-paths"></a>Rutas de acceso completas  
 Donde los nombres de archivos o directorios se especifican como argumentos, deben ser rutas de acceso completas o rutas de acceso UNC, sin las barras diagonales inversas finales. Es responsabilidad del código fuente del complemento de control para traducir a rutas de acceso relativas si es un requisito del sistema de control de origen subyacente.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Especifique una ruta de acceso completa para el archivo DLL registrada  
 El IDE ya no carga los archivos DLL de rutas de acceso relativas (por ejemplo,.\NewProvider.dll). Debe especificarse una ruta de acceso completa del archivo DLL (por ejemplo, C:\Providers\NewProvider.dll). Este requisito refuerza la seguridad del IDE al impedir la carga de archivos DLL de controles de origen suplantadas o no autorizados.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Busque un complemento de VSSCI existente al instalar el complemento de Control de código fuente  
 Un usuario que tiene previsto instalar el complemento de control de código fuente ya puede tener un control de origen existente complemento instalado en el equipo. El programa de instalación (programa de instalación) para el complemento que cree debe determinar si hay valores existentes para las claves del registro pertinentes. Si ya están establecidas estas claves, el programa de instalación debe pedir al usuario si se debe registrar el complemento como el complemento de control de código fuente de forma predeterminada y reemplazar uno que ya está instalado.  
  
## <a name="error-result-codes-and-reporting"></a>Códigos de resultado de error e informes  
 El `SCC_OK` devolver el código de una función de control de origen indica que la operación se ha realizado correctamente para todos los archivos. Si se produce un error en la operación, se debe devolver el último código de error encontrado.  
  
 La regla para los informes es que, si se produce un error en el IDE, el IDE es responsable de informar de una. Si se produce un error en el sistema de control de código fuente, el complemento de control de código fuente es responsable de informar de él. Por ejemplo, "ningún archivo actualmente seleccionado" se notificarían por el IDE, mientras que "este archivo ya está desprotegido por" que se notificarían por el complemento.  
  
## <a name="the-context-structure"></a>La estructura de contexto  
 Durante la llamada a la [SccInitialize](../extensibility/sccinitialize-function.md), las fases de llamador el `ppvContext` parámetro, que es un identificador a un void no inicializado. El complemento de control de código fuente puede omitir este parámetro o se puede asignar una estructura de cualquier tipo y colocar un puntero a esa estructura en el puntero pasado. El IDE no entiende esta estructura, pero pasa un puntero a esta estructura en todas las llamadas en el complemento. Esto proporciona información de la caché de contexto valioso para el complemento que puede usar para mantener la información de estado global que se conserve entre las llamadas de función sin usar las variables globales. El complemento es responsable de liberar la estructura en una llamada a la [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Si el complemento establece el `SCC_CAP_REENTRANT` bit en el [SccInitialize](../extensibility/sccinitialize-function.md) (específicamente, en el `lpSccCaps` parámetro), varias estructuras de contexto se utilizan para realizar un seguimiento de todos los proyectos que están abiertos.  
  
## <a name="bitflags-and-other-command-options"></a>Marcadores de bits y otras opciones de comando  
 Para cada comando, como el [SccGet](../extensibility/sccget-function.md), el IDE puede especificar muchas opciones que modifiquen el comportamiento del comando.  
  
 La API admite la configuración de determinadas opciones por el IDE a través de la `fOptions` parámetro. Estas opciones se describen en [marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) junto con los comandos que afectan. En general, estas son opciones para el que el usuario no se le solicita.  
  
 Opciones de configuración más configurables por el usuario no se definen de esta manera, porque varían enormemente entre los complementos de control de código fuente. Por lo tanto, es el mecanismo recomendado un **avanzadas** botón. Por ejemplo, en el **obtener** el IDE muestra el cuadro de diálogo, sólo la información que lo entiende, pero también muestra un **avanzadas** botón si el complemento tiene opciones para este comando. Cuando el usuario hace clic en el **avanzadas** button, las llamadas IDE el [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) para habilitar el complemento para preguntar al usuario información acerca de los marcadores de bits o de fecha y hora de control de código fuente. El complemento devuelve esta información en una estructura que se pasa durante la `SccGet` comando.  
  
## <a name="see-also"></a>Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [Creación de un complemento de control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md)
