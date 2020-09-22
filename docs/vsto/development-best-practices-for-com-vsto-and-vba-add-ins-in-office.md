---
title: 'Prácticas recomendadas de desarrollo: COM, VSTO, & complementos VBA en Office'
ms.date: 07/25/2017
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be48e7ce721c84656362a019e0cc5eec1ae2ee17
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808212"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Prácticas recomendadas de desarrollo para complementos COM, VSTO y VBA en Office
  Si va a desarrollar complementos COM, VSTO o VBA para Office, siga las prácticas recomendadas de desarrollo descritas en este artículo.   Esto le ayudará a garantizar:

- Compatibilidad de los complementos en diferentes versiones e implementaciones de Office.
- Reducción de la complejidad de la implementación de complementos para los usuarios y los administradores de ti.
- No se producen errores de instalación no intencionada o de tiempo de ejecución del complemento.

>Nota: no se admite el uso del [puente de escritorio](/windows/uwp/porting/desktop-to-uwp-root) para preparar el complemento com, VSTO o VBA para la tienda Windows. Los complementos COM, VSTO y VBA no se pueden distribuir en la tienda Windows ni en la tienda Office.

## <a name="do-not-check-for-office-during-installation"></a>No buscar Office durante la instalación
 No se recomienda que el complemento detecte si Office se instala durante el proceso de instalación del complemento. Si Office no está instalado, puede instalar el complemento y el usuario podrá tener acceso a él una vez instalado Office.

## <a name="use-embedded-interop-types-nopia"></a>Usar tipos de interoperabilidad incrustados (NoPIA)
Si la solución usa .NET 4,0 o una versión posterior, use tipos de interoperabilidad incrustados (NoPIA) en lugar de, en función del redistribuible de ensamblados de interoperabilidad primarios (PIA) de Office. El uso de la inserción de tipos reduce el tamaño de la instalación de la solución y garantiza la compatibilidad futura. Office 2010 era la última versión de Office que incluía el PIA Redistributable. Para obtener más información, vea [Tutorial: incrustar información de tipos de ensamblados de Microsoft Office](/previous-versions/ee317478(v=vs.140)) y [tipos de interoperabilidad incrustados](/windows/uwp/porting/desktop-to-uwp-root).

Si la solución usa una versión anterior de .NET, se recomienda que actualice la solución para usar .NET 4,0 o posterior. El uso de .NET 4,0 o posterior reduce los requisitos previos de tiempo de ejecución en las versiones más recientes de Windows.

## <a name="avoid-depending-on-specific-office-versions"></a>Evitar en función de las versiones específicas de Office
Si la solución usa una funcionalidad que solo está disponible en las versiones más recientes de Office, compruebe que la capacidad existe (si es posible, en el nivel de característica) en tiempo de ejecución (por ejemplo, mediante el control de excepciones o la comprobación de la versión). Valide las versiones mínimas, en lugar de las versiones específicas, mediante las API admitidas en el modelo de objetos, como la [propiedad Application. version](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). No se recomienda confiar en los metadatos binarios de Office, las rutas de acceso de instalación o las claves del registro, ya que pueden cambiar entre instalaciones, entornos y versiones.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Habilitar el uso de Office de 32 y de 64 bits
El destino de compilación predeterminado debe ser compatible con 32 bits (x86) y 64 bits (x64), a menos que la solución dependa de bibliotecas que solo están disponibles para un valor de bits específico. La versión de Office de 64 bits está aumentando en la adopción, especialmente en entornos de macrodatos. La compatibilidad con 32 bits y 64 bits facilita a los usuarios la transición entre las versiones de Office de 32 bits y de 64 bits.

Al escribir código VBA, use instrucciones de declaración seguras de 64 bits y variables de conversión, según corresponda. Además, asegúrese de que los documentos se pueden compartir entre los usuarios que ejecutan las versiones de 32 de bits o de 64 bits de Office proporcionando código para cada tipo de bits. Para obtener más información, [64 vea información general de Visual Basic bits para aplicaciones](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Compatibilidad con entornos restringidos
La solución no debe requerir privilegios de administrador o elevación de la cuenta de usuario. Además, la solución no debe depender de establecer o modificar:

- El directorio de trabajo actual.
- Directorios de carga de archivos DLL.
- Variable de ruta de acceso.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Cambiar la ubicación de guardado de la configuración y los datos compartidos
Si la solución está formada por un complemento y un proceso externo a Office, no use la carpeta de datos de la aplicación del usuario ni el registro para intercambiar datos o configuraciones entre el complemento y el proceso externo. En su lugar, considere la posibilidad de usar la carpeta temporal del usuario, la carpeta documentos o el directorio de instalación de la solución.

## <a name="increment-the-version-number-with-each-update"></a>Incrementar el número de versión con cada actualización
Establezca el número de versión de los archivos binarios de la solución y péguelo en cada actualización. Esto facilitará a los usuarios la identificación de los cambios entre las versiones y la evaluación de la compatibilidad.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Proporcionar instrucciones de soporte técnico para las versiones más recientes de Office
Los clientes están pidiendo a los ISV que proporcionen instrucciones de soporte técnico para los complementos COM, VSTO y VBA que se ejecutan en Office. La lista de las instrucciones de soporte explícito ayuda a los clientes que usan Microsoft 365 aplicaciones para herramientas de preparación empresarial a comprender su soporte técnico.

Para proporcionar instrucciones de soporte técnico para las aplicaciones cliente de Office (por ejemplo, Word o Excel), compruebe primero que los complementos se ejecutan en la versión actual de Office y, a continuación, confirme para proporcionar actualizaciones si el complemento se interrumpe en una versión futura. No es necesario probar los complementos cuando Microsoft publica una nueva compilación o una actualización de Office. Microsoft no suele cambiar la plataforma de extensibilidad COM, VSTO y VBA en Office, y estos cambios se documentan bien.

>Importante: Microsoft mantiene una lista de complementos admitidos para los informes de disponibilidad e información de contacto de ISV. Para obtener la lista de complementos, vea [/ConfigMgr/Desktop-Analytics/Ready-for-Windows](/configmgr/desktop-analytics/ready-for-windows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Usar el monitor de procesos para ayudar a depurar problemas de instalación o carga
Si el complemento tiene problemas de compatibilidad durante la instalación o la carga, pueden estar relacionados con problemas con el acceso al registro o al archivo. Use el [monitor de procesos](/sysinternals/downloads/procmon) o una herramienta de depuración similar para registrar y comparar el comportamiento en un entorno de trabajo para ayudar a identificar el problema.