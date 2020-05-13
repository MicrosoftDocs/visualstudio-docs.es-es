---
title: 'Cómo: Especificar una ubicación alternativa para las actualizaciones de implementación Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0484e36bb857f5d08382f86f42b2e09dda21616
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037342"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Cómo: Especificar una ubicación alternativa para las actualizaciones de la implementación
Puede instalar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la aplicación inicialmente desde un CD o un recurso compartido de archivos, pero la aplicación debe buscar actualizaciones periódicas en la Web. Puede especificar una ubicación alternativa para las actualizaciones en el manifiesto de implementación para que la aplicación pueda actualizarse desde la Web después de su instalación inicial.

> [!NOTE]
> La aplicación debe estar configurada para instalarse localmente para usar esta característica. Para obtener más información, vea [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Además, si [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instala una aplicación desde la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] red, establecer una ubicación alternativa hace que use esa ubicación tanto para la instalación inicial como para todas las actualizaciones posteriores. Si instala la aplicación localmente (por ejemplo, desde un CD), la instalación inicial se realiza con el medio original y todas las actualizaciones posteriores usarán la ubicación alternativa.

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Especificar una ubicación alternativa para las actualizaciones mediante MageUI.exe (utilidad basada en formularios Windows Forms)

1. Abra un símbolo del sistema de .NET Framework y escriba:

     **mageui.exe**

2. En el menú **Archivo,** elija **Abrir** para abrir el manifiesto de implementación de la aplicación.

3. Seleccione la pestaña **Opciones de implementación**.

4. En el cuadro de texto denominado **Ubicación de inicio**, escriba la dirección URL del directorio que contendrá el manifiesto de implementación para las actualizaciones de la aplicación.

5. Guarde el manifiesto de implementación.

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Especifique una ubicación alternativa para las actualizaciones mediante Mage.exe

1. Abra un símbolo del sistema de .NET Framework.

2. Establezca la ubicación de actualización mediante el siguiente comando. En este ejemplo, *HelloWorld.exe.application* es [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la ruta de acceso al manifiesto `http://adatum.com/Update/Path` de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, que siempre tiene la extensión .application y es la dirección URL que comprobará si hay actualizaciones de la aplicación.

    **Mage -Update HelloWorld.exe.application -ProviderUrl http:\//adatum.com/Update/Path**

3. Guarde el archivo.

   > [!NOTE]
   > Ahora debe volver a firmar el archivo con *Mage.exe*. Para obtener más información, vea [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="net-framework-security"></a>Seguridad de .NET Framework
 Si instala la aplicación desde un medio sin conexión, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] como un CD, y `<deploymentProvider>` el equipo está en línea, comprueba primero la dirección URL especificada por la etiqueta en el manifiesto de implementación para determinar si la ubicación de actualización contiene una versión más reciente de la aplicación. Si lo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] hace, instala la aplicación directamente desde allí, en lugar del directorio de instalación inicial, y `<deploymentProvider>`Common Language Runtime (CLR) determina el nivel de confianza de la aplicación mediante . Si el equipo está `<deploymentProvider>` sin [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] conexión o no se puede acceder a ella, se instala desde el CD y CLR concede confianza en función del punto de instalación; para una instalación de CD, esto significa que su aplicación recibe plena confianza. Todas las actualizaciones posteriores heredarán ese nivel de confianza.

 Todas [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las `<deploymentProvider>` aplicaciones que usan deben declarar explícitamente los permisos que necesitan en su manifiesto de aplicación, de modo que la aplicación no reciba diferentes niveles de confianza en equipos diferentes.

## <a name="see-also"></a>Consulte también
- [Tutorial: Implementación manual de una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Manifiesto de implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Protección de las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)
- [Selección de una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)