---
title: "Procedimientos recomendados para implementar un complemento de Control de código fuente | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9099d652012fb8b45b7b79f9c620f4102e7af602
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Procedimientos recomendados para implementar un complemento de Control de código fuente
Los detalles técnicos siguientes pueden ayudarle a implementar un complemento de control de código fuente de forma confiable [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="memory-management-issues"></a>Problemas de administración de memoria  
 En la mayoría de los casos, el entorno de desarrollo integrado (IDE), que es el autor de la llamada, se libera y asigna memoria. El complemento de control de código fuente devuelve cadenas y otros elementos de búferes asignados al llamador. Las excepciones se indican en las descripciones de funciones concretas donde aparecen.  
  
## <a name="arrays-of-file-names"></a>Matrices de nombres de archivo  
 Cuando se pasa una matriz de archivos, no se pasa como una matriz contigua de nombres de archivo. Se pasa como una matriz de punteros a los nombres de archivo. Por ejemplo, en la [SccGet](../extensibility/sccget-function.md), los nombres de archivo se pasan por la `lpFileNames` parámetro, donde `lpFileNames` es realmente un puntero a un `char **`. `lpFileNames`[0] es un puntero a first name, `lpFileNames`[1] es un puntero para el nombre del segundo y así sucesivamente.  
  
## <a name="large-model"></a>Modelos grandes  
 Todos los punteros son de 32 bits, incluso en sistemas operativos de 16 bits.  
  
## <a name="fully-qualified-paths"></a>Rutas de acceso completas  
 Donde los nombres de archivos o directorios se especifican como argumentos, deben ser rutas de acceso completas o rutas de acceso UNC, sin las barras diagonales inversas finales. Es responsabilidad del origen del complemento de control para traducir a rutas de acceso relativas si es un requisito del sistema de control de origen subyacente.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Especifique una ruta de acceso completa para el archivo DLL registrada  
 El IDE ya no carga archivos DLL de rutas de acceso relativas (por ejemplo,.\NewProvider.dll). Debe especificarse una ruta de acceso completa del archivo DLL (por ejemplo, C:\Providers\NewProvider.dll). Este requisito refuerza la seguridad del IDE evitando la carga de archivos DLL de controles de origen no autorizados o suplantado.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Busque un complemento de VSSCI existente cuando se instala el complemento de Control de código fuente  
 Un usuario que tiene previsto instalar el complemento de control de código fuente ya puede tener un origen control existente complemento instalado en el equipo. El programa de instalación del complemento que cree debe determinar si existen valores existentes para las claves del registro. Si ya se establecen estas claves, el programa de instalación debe pedir al usuario si desea registrar el complemento como el complemento de control de código fuente de forma predeterminada y reemplazar al que ya está instalado.  
  
## <a name="error-result-codes-and-reporting"></a>Códigos de resultado de error e informes  
 El `SCC_OK` devuelve el código de una función de control de origen indica que la operación se ha realizado correctamente para todos los archivos. Si se produce un error en la operación, se espera para devolver el último código de error encontrado.  
  
 La regla de informes es que, si se produce un error en el IDE, el IDE es responsable de informar de él. Si se produce un error en el sistema de control de código fuente, el complemento de control de código fuente es responsable de informar de él. Por ejemplo, "no hay archivos seleccionados actualmente", se mostrarían por el IDE, mientras que "este archivo ya está desprotegido", se mostrarían el complemento.  
  
## <a name="the-context-structure"></a>La estructura de contexto  
 Durante la llamada a la [SccInitialize](../extensibility/sccinitialize-function.md), el llamador pasa la `ppvContext` parámetro, que es un identificador para un parámetro void sin inicializar. El complemento de control de código fuente puede pasar por alto este parámetro o se puede asignar una estructura de cualquier tipo y colocar un puntero a esa estructura en el puntero ha pasado. El IDE no entiende esta estructura, pero pasa un puntero a esta estructura en todas las llamadas en el complemento. Esto proporciona información de la caché de contexto valiosos en el complemento que puede utilizar para mantener la información de estado global que se conserva entre las llamadas a funciones sin el uso de variables globales. El complemento es responsable de liberar la estructura en una llamada a la [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Si el complemento se establece el `SCC_CAP_REENTRANT` de bits en el [SccInitialize](../extensibility/sccinitialize-function.md) (específicamente, en la `lpSccCaps` parámetro), varias estructuras de contexto se utilizan para realizar un seguimiento de todos los proyectos que están abiertos.  
  
## <a name="bitflags-and-other-command-options"></a>Marcadores de bits y otras opciones de comando  
 Para cada comando, como el [SccGet](../extensibility/sccget-function.md), el IDE puede especificar muchas opciones que modifiquen el comportamiento del comando.  
  
 La API es compatible con la configuración de determinadas opciones por el IDE a través de la `fOptions` parámetro. Estas opciones se describen en [marcadores de bits utilizado por determinados comandos](../extensibility/bitflags-used-by-specific-commands.md) junto con los comandos que afectan a. En general, estas son opciones que el usuario no se le solicita.  
  
 Más opciones de configuración configurables por el usuario no se definen de esta manera, porque varían enormemente entre los complementos de control de código fuente. Por lo tanto, el mecanismo recomendado es un **avanzadas** botón. Por ejemplo, en la **obtener** cuadro de diálogo, el IDE muestra sólo la información que entienda, pero también muestra un **avanzadas** botón si el complemento tiene opciones para este comando. Cuando el usuario hace clic en el **avanzadas** botón, el IDE llama el [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) para habilitar el complemento para pedir al usuario para obtener información, como marcadores de bits o una fecha y hora de control de código fuente. El complemento devuelve esta información en una estructura que se pasa durante la `SccGet` comando.  
  
## <a name="see-also"></a>Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [Creación de un complemento de control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md)