---
title: Prácticas recomendadas de desarrollo de COM, VSTO y VBA complementos de Office
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
ms.openlocfilehash: b81dec69d27cc32fa5e6848d358049d8b8e2c04e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643579"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Prácticas recomendadas de desarrollo de COM, VSTO y VBA complementos de Office
  Si está desarrollando complementos COM, VSTO o VBA para Office, siga las prácticas recomendadas de desarrollo se describe en este artículo.   Esto ayudará a garantizar:

-  Compatibilidad de los complementos a través de diferentes versiones e implementaciones de Office.
-  Menor complejidad de implementación de complementos para los usuarios y administradores de TI.
-  No se producen errores de instalación o en tiempo de ejecución no deseadas de su complemento.

>Nota: Mediante el [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root) para preparar su COM, VSTO o VBA complemento para el Store de Windows no es compatible. No se puede distribuir complementos COM, VSTO y VBA en el Store de Windows o el Store de Office.

## <a name="do-not-check-for-office-during-installation"></a>No busque Office durante la instalación
 No se recomienda tener el complemento detecta si está instalado Office durante el proceso de instalación del complemento. Si Office no está instalado, puede instalar el complemento y el usuario podrá acceder a él después de instalar Office.

## <a name="use-embedded-interop-types-nopia"></a>Usar tipos de interoperabilidad incrustados (NoPIA)
Si la solución utiliza .NET 4.0 o versiones posteriores, utilice tipos de interoperabilidad incrustados (NoPIA) en lugar de según el Office principal interoperabilidad ensamblados (PIA) redistribuible. Con la inserción de tipos reduce el tamaño de la instalación de la solución y garantiza la compatibilidad con versiones futura. Office 2010 fue la última versión de Office que distribuye el paquete redistribuible de PIA. Para obtener más información, vea [Tutorial: Incrustar información de tipos desde ensamblados de Microsoft Office](https://msdn.microsoft.com/library/ee317478.aspx) y [equivalencia de tipos y tipos de interoperabilidad incrustados](/windows/uwp/porting/desktop-to-uwp-root).

Si la solución usa una versión anterior de. NET, se recomienda que actualice su solución para usar .NET 4.0 o posterior. El uso de .NET 4.0 o posterior reduce los requisitos previos de tiempo de ejecución en las versiones más recientes de Windows.

## <a name="avoid-depending-on-specific-office-versions"></a>Evitar la dependencia de versiones específicas de Office
Si la solución usa la funcionalidad que solo está disponible en las versiones más recientes de Office, compruebe que existe la capacidad (si es posible, en el nivel de función) en tiempo de ejecución (por ejemplo, el uso del control o mediante la comprobación de la versión de excepciones). Validar las versiones mínimas, en lugar de versiones específicas, mediante las API compatibles en el modelo de objetos, como el [Application.Version propiedad](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). No se recomienda depender metadatos binaria, las rutas de acceso de instalación o las claves del registro de Office ya que pueden cambiar entre las instalaciones, los entornos y las versiones.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Habilitar el uso de Office de 32 bits y 64 bits
El destino de compilación predeterminado debe admitir (x86) 32 bits y 64 bits (x64), a menos que la solución depende de las bibliotecas que solo están disponibles para un valor específico de bits. La versión de 64 bits de Office está aumentando en la adopción, especialmente en entornos de macrodatos. Soporte de 32 bits y 64 bits facilita a los usuarios para realizar la transición entre las versiones de 32 bits y 64 bits de Office.

Al escribir código VBA, uso seguro de 64 bits instrucciones declare y convertir variables según corresponda. Además, asegúrese de que los documentos se pueden compartir entre los usuarios que ejecutan versiones de 32 bits o 64 bits de Office al proporcionar código para cada valor de bits. Para obtener más información, consulte [Visual Basic de 64 bits para información general sobre aplicaciones](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Compatibilidad con entornos restringidos
La solución no debería requerir privilegios de administrador o la elevación de la cuenta de usuario. Además, la solución no debe depender establecer o modificar:

- El directorio de trabajo actual.
- Directorios de la carga DLL.
- La variable PATH.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Cambiar la operación de guardar la ubicación de datos compartidos y configuración
Si la solución consta de un complemento y un proceso externo a Office, no use el registro o carpeta de datos de aplicación del usuario para intercambiar datos o la configuración entre el complemento y el proceso externo. En su lugar, considere el uso de la carpeta temporal del usuario, la carpeta documentos o directorio de instalación de la solución.

## <a name="increment-the-version-number-with-each-update"></a>Incremente el número de versión con cada actualización
Establecer el número de versión de los archivos binarios de la solución e incrementarlo con cada actualización. Así resultará más fácil para los usuarios identificar los cambios entre las versiones y evaluar la compatibilidad.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Proporcionar instrucciones de compatibilidad para las versiones más recientes de Office
Los clientes están solicitando los ISV que proporcionen declaraciones de compatibilidad para sus COM, VSTO y VBA complementos que se ejecutan en Office. Enumerar su compatibilidad explícita con las instrucciones le ayuda a los clientes que usan Office 365 ProPlus herramientas de preparación para comprender el soporte técnico.

Para proporcionar compatibilidad con instrucciones para las aplicaciones cliente de Office (por ejemplo, Word o Excel), primero compruebe que los complementos se ejecutan en la versión actual de Office y, a continuación, confirmación para proporcionar actualizaciones si el complemento se interrumpe en una versión futura. No es necesario que probar los complementos cuando Microsoft publica una nueva compilación o una actualización de Office. Microsoft no suele cambia la plataforma de extensibilidad de COM, VSTO y VBA en Office y se documentará también estos cambios.

>Importante: Microsoft mantiene una lista de complementos compatibles para los informes de disponibilidad e información de contacto de ISV. Para obtener el complemento enumerado, consulte [ https://aka.ms/readyforwindows ](https://aka.ms/readyforwindows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Utilice el Monitor de proceso para ayudar a depurar la instalación o cargando problemas
Si el complemento tiene problemas de compatibilidad durante la instalación o la carga, podría deberse a problemas de acceso de archivo o del registro. Use [Process Monitor](/sysinternals/downloads/procmon) o una herramienta de depuración similar para registrar y comparar el comportamiento de un entorno de trabajo para ayudar a identificar el problema.
