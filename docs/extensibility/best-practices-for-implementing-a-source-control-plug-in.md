---
title: 'Implementar un complemento de control de código fuente: procedimientos recomendados'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 399afaff75b2456e668aaa9862fb7aa5439cc39f
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038457"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Prácticas recomendadas para implementar un complemento de control de código fuente
Los detalles técnicos siguientes pueden ayudarle a implementar de forma confiable un complemento de control de código fuente en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="memory-management-issues"></a>Problemas de administración de memoria
 En la mayoría de los casos, el entorno de desarrollo integrado (IDE), que es el autor de la llamada, libera y asigna memoria. El complemento de control de código fuente devuelve cadenas y otros elementos en búferes asignados por el autor de la llamada. Las excepciones se indican en las descripciones de funciones específicas en las que se producen.

## <a name="arrays-of-file-names"></a>Matrices de nombres de archivo
 Cuando se pasa una matriz de archivos, no se pasa como una matriz contigua de nombres de archivo. Se pasa como una matriz de punteros a los nombres de archivo. Por ejemplo, en [SccGet](../extensibility/sccget-function.md), los nombres de archivo se pasan mediante el `lpFileNames` parámetro, donde `lpFileNames` es realmente un puntero a `char **` . `lpFileNames`[0] es un puntero al nombre, `lpFileNames` [1] es un puntero al segundo nombre, etc.

## <a name="large-model"></a>Modelo grande
 Todos los punteros son de 32 bits, incluso en sistemas operativos de 16 bits.

## <a name="fully-qualified-paths"></a>Rutas de acceso completas
 Cuando los nombres de archivo o los directorios se especifican como argumentos, deben ser rutas de acceso completas o rutas UNC, sin las barras diagonales inversas. Es responsabilidad del complemento de control de código fuente trasladarlos a rutas de acceso relativas si es un requisito del sistema de control de código fuente subyacente.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Especifique una ruta de acceso completa para el archivo DLL registrado
 El IDE ya no carga los archivos dll desde las rutas de acceso relativas (por ejemplo, *.\NewProvider.dll*). Se debe especificar una ruta de acceso completa del archivo DLL (por ejemplo, *C:\Providers\NewProvider.dll*). Este requisito fortalece la seguridad del IDE al impedir la carga de archivos dll de control de código fuente no autorizados o suplantados.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Buscar un complemento de VSSCI existente al instalar el complemento de control de código fuente
 Es posible que un usuario que planea instalar el complemento de control de código fuente ya tenga instalado en el equipo un complemento de control de código fuente existente. El programa de instalación (programa de instalación) para el complemento que cree debe determinar si hay valores existentes para las claves del registro correspondientes. Si estas claves ya están establecidas, el programa de instalación debería preguntar al usuario si desea registrar el complemento como el complemento de control de código fuente predeterminado y reemplazar el que ya está instalado.

## <a name="error-result-codes-and-reporting"></a>Códigos de resultado de error e informes
 El `SCC_OK` código de retorno para una función de control de código fuente indica que la operación se ha realizado correctamente para todos los archivos. Si se produce un error en la operación, se espera que devuelva el último código de error encontrado.

 La regla para la generación de informes es que si se produce un error en el IDE, el IDE es responsable de la notificación. Si se produce un error en el sistema de control de código fuente, el complemento de control de código fuente es responsable del informe. Por ejemplo, el IDE no informará de **ningún archivo seleccionado actualmente** , mientras que **este archivo ya está desprotegido** por el complemento.

## <a name="the-context-structure"></a>La estructura de contexto
 Durante la llamada a [SccInitialize](../extensibility/sccinitialize-function.md), el llamador pasa el `ppvContext` parámetro, que es un identificador no inicializado para un void. El complemento de control de código fuente puede omitir este parámetro o puede asignar una estructura de cualquier tipo y colocar un puntero a esa estructura en el puntero pasado. El IDE no entiende esta estructura, pero pasa un puntero a esta estructura en cada otra llamada del complemento. Esto proporciona información valiosa de la caché de contexto al complemento que puede usar para mantener la información de estado global que se mantiene entre las llamadas de función sin usar variables globales. El complemento es responsable de liberar la estructura en una llamada a [SccUninitialize](../extensibility/sccuninitialize-function.md).

 Si el complemento establece el `SCC_CAP_REENTRANT` bit en el [SccInitialize](../extensibility/sccinitialize-function.md) (concretamente, en el `lpSccCaps` parámetro), se usan varias estructuras de contexto para realizar el seguimiento de todos los proyectos que están abiertos.

## <a name="bitflags-and-other-command-options"></a>Marcadores y otras opciones de comando
 Para cada comando, como [SccGet](../extensibility/sccget-function.md), el IDE puede especificar muchas opciones que cambian el comportamiento del comando.

 La API admite la configuración de determinadas opciones por el IDE a través del `fOptions` parámetro. Estas opciones se describen en [marcadores que usan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) junto con los comandos a los que afectan. En general, se trata de opciones para las que no se debería preguntar al usuario.

 La mayoría de las opciones de configuración configurables por el usuario no se definen de esta manera, porque varían considerablemente entre los complementos de control de código fuente. Por lo tanto, el mecanismo recomendado es un botón **avanzado** . Por ejemplo, en el cuadro de diálogo **obtener** , el IDE muestra solo la información que entiende, pero también muestra un botón **avanzado** si el complemento tiene opciones para este comando. Cuando el usuario hace clic en el botón **avanzadas** , el IDE llama a [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) para habilitar el complemento de control de código fuente para solicitar información al usuario, como marcadores o una fecha y hora. El complemento devuelve esta información en una estructura que se pasa en el `SccGet` comando.

## <a name="see-also"></a>Consulte también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [Crear un complemento de control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md)
