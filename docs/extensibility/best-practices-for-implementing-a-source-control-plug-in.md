---
title: Prácticas recomendadas para implementar un complemento de control de código fuente Microsoft Docs
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
ms.openlocfilehash: 68491f22d63ae3ebb664b7c22188a661dccbf39a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740056"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Prácticas recomendadas para implementar un complemento de control de código fuente
Los siguientes detalles técnicos pueden ayudarle a implementar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]de forma fiable un complemento de control de código fuente.

## <a name="memory-management-issues"></a>Problemas de administración de memoria
 En la mayoría de los casos, el entorno de desarrollo integrado (IDE), que es el autor de la llamada, libera y asigna memoria. El complemento de control de código fuente devuelve cadenas y otros elementos en búferes asignados por el autor de la llamada. Las excepciones se indican en las descripciones de funciones específicas donde se producen.

## <a name="arrays-of-file-names"></a>Matrices de nombres de archivo
 Cuando se pasa una matriz de archivos, no se pasa como una matriz contigua de nombres de archivo. Se pasa como una matriz de punteros a los nombres de archivo. Por ejemplo, en [SccGet](../extensibility/sccget-function.md), el `lpFileNames` parámetro pasa `lpFileNames` los nombres de `char **`archivo, donde en realidad es un puntero a un archivo . `lpFileNames`[0] es un puntero al `lpFileNames`primer nombre, [1] es un puntero al segundo nombre, y así sucesivamente.

## <a name="large-model"></a>Modelo grande
 Todos los punteros son de 32 bits, incluso en sistemas operativos de 16 bits.

## <a name="fully-qualified-paths"></a>Rutas totalmente calificadas
 Cuando los nombres de archivo o directorios se especifican como argumentos, deben ser rutas de acceso completas o rutas UNC, sin las barras diagonales inversas finales. Es responsabilidad del complemento de control de código fuente traducirlos a rutas de acceso relativas si se trata de un requisito del sistema de control de código fuente subyacente.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Especifique una ruta de acceso completa para el archivo DLL registrado
 El IDE ya no carga archivos DLL desde rutas de acceso relativas (por ejemplo, *.-NewProvider.dll*). Se debe especificar una ruta de acceso completa del archivo DLL (por ejemplo, *C:-Providers-NewProvider.dll*). Este requisito refuerza la seguridad del IDE al impedir la carga de archivos DLL de control de código fuente no autorizados o suplantados.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Compruebe si hay un complemento VSSCI existente al instalar el complemento de control de código fuente
 Un usuario que planea instalar el complemento de control de código fuente ya puede tener un complemento de control de código fuente existente instalado en el equipo. El programa de instalación (configuración) para el complemento que cree debe determinar si existen valores para las claves de registro relevantes. Si estas claves ya están establecidas, el programa de instalación debe preguntar al usuario si desea registrar el complemento como el complemento de control de código fuente predeterminado y reemplazar el que ya está instalado.

## <a name="error-result-codes-and-reporting"></a>Códigos de resultado de error e informes
 El `SCC_OK` código de retorno de una función de control de código fuente indica que la operación se ha realizado correctamente para todos los archivos. Si se produce un error en la operación, se espera que devuelva el último código de error encontrado.

 La regla para informar es que si se produce un error en el IDE, el IDE es responsable de notificarlo. Si se produce un error en el sistema de control de código fuente, el complemento de control de código fuente es responsable de notificarlo. Por ejemplo, el IDE no **notificaría ningún archivo actualmente,** mientras que **este archivo ya está desprotegido** sería notificado por el complemento.

## <a name="the-context-structure"></a>La estructura del contexto
 Durante la llamada a [SccInitialize](../extensibility/sccinitialize-function.md), `ppvContext` el llamador pasa el parámetro, que es un identificador no inicializado a un void. El complemento de control de código fuente puede omitir este parámetro o puede asignar una estructura de cualquier tipo y colocar un puntero a esa estructura en el puntero pasado. El IDE no entiende esta estructura, pero pasa un puntero a esta estructura en cada otra llamada en el complemento. Esto proporciona información valiosa de caché de contexto al complemento que puede usar para mantener la información de estado global que persiste en las llamadas de función sin usar variables globales. El plug-in es responsable de liberar la estructura en una llamada a la [SccUninitialize](../extensibility/sccuninitialize-function.md).

 Si el complemento establece `SCC_CAP_REENTRANT` el bit en [SccInitialize](../extensibility/sccinitialize-function.md) (específicamente, en el `lpSccCaps` parámetro), se utilizan varias estructuras de contexto para realizar un seguimiento de todos los proyectos que están abiertos.

## <a name="bitflags-and-other-command-options"></a>Bitflags y otras opciones de comando
 Para cada comando, como [SccGet](../extensibility/sccget-function.md), el IDE puede especificar muchas opciones que cambian el comportamiento del comando.

 La API admite la configuración de determinadas `fOptions` opciones mediante el IDE a través del parámetro. Estas opciones se describen en [Bitflags utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) junto con los comandos que afectan. En general, se trata de opciones para las que no se solicitaría al usuario.

 La mayoría de las opciones de configuración configurables por el usuario no se definen de esta manera, ya que varían ampliamente entre los complementos de control de código fuente. Por lo tanto, el mecanismo recomendado es un botón **Avanzado.** Por ejemplo, en el cuadro de diálogo **Obtener,** el IDE muestra solo la información que comprende, pero también muestra un botón **Avanzado** si el complemento tiene opciones para este comando. Cuando el usuario hace clic en **el** avanzado botón, el IDE llama a la [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) para habilitar el complemento de control de código fuente para solicitar al usuario información, como bitflags o una fecha y hora. El complemento devuelve esta información en una estructura `SccGet` que se devuelve durante el comando.

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [Crear un complemento de control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md)
