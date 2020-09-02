---
title: 'Cómo: especificar una ubicación alternativa para las actualizaciones de implementación | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b6388833e6574fc1d631d391fa7b67d5f0a3372
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "82037225"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Cómo: Especificar una ubicación alternativa para las actualizaciones de la implementación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede instalar la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación inicialmente desde un CD o un recurso compartido de archivos, pero la aplicación debe comprobar si hay actualizaciones periódicas en la Web. Puede especificar una ubicación alternativa para las actualizaciones en el manifiesto de implementación para que la aplicación pueda actualizarse desde la web después de la instalación inicial.  
  
> [!NOTE]
> La aplicación debe estar configurada para instalarse localmente para usar esta característica. Para obtener más información, vea [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Además, si instala una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación desde la red, el establecimiento de una ubicación alternativa hace que [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] use esa ubicación para la instalación inicial y todas las actualizaciones posteriores. Si instala la aplicación localmente (por ejemplo, desde un CD), la instalación inicial se realiza con el medio original y todas las actualizaciones posteriores usarán la ubicación alternativa.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Especificar una ubicación alternativa para las actualizaciones mediante MageUI.exe (utilidad basada en Windows Forms)  
  
1. Abra una .NET Framework símbolo del sistema y escriba:  
  
     **mageui.exe**  
  
2. En el menú **archivo** , elija **abrir** para abrir el manifiesto de implementación de la aplicación.  
  
3. Seleccione la pestaña **Opciones de implementación**.  
  
4. En el cuadro de texto denominado **Ubicación de inicio**, escriba la dirección URL del directorio que contendrá el manifiesto de implementación para las actualizaciones de la aplicación.  
  
5. Guarde el manifiesto de implementación.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Especificar una ubicación alternativa para las actualizaciones mediante Mage.exe  
  
1. Abra una .NET Framework símbolo del sistema.  
  
2. Establezca la ubicación de la actualización con el siguiente comando. En este ejemplo, **HelloWorld.exe. Application** es la ruta de acceso al [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifiesto de aplicación, que siempre tiene la extensión. Application, y `http://adatum.com/Update/Path` es la dirección URL que comprobará [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] las actualizaciones de la aplicación.  
  
     **Mage-Update HelloWorld.exe. Application-ProviderUrl http: \/ /adatum.com/update/path**  
  
3. Guarde el archivo.  
  
    > [!NOTE]
    > Ahora debe volver a firmar el archivo con Mage.exe. Para obtener más información, vea [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Si instala la aplicación desde un medio sin conexión, como un CD, y el equipo está en línea, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] comprueba primero la dirección URL especificada por la `<deploymentProvider>` etiqueta en el manifiesto de implementación para determinar si la ubicación de actualización contiene una versión más reciente de la aplicación. Si lo hace, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instala la aplicación directamente desde allí, en lugar de desde el directorio de instalación inicial, y el Common Language Runtime (CLR) determina el nivel de confianza de la aplicación mediante `<deploymentProvider>` . Si el equipo está sin conexión o `<deploymentProvider>` es inaccesible, se [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instala desde el CD y CLR concede confianza en función del punto de instalación; para una instalación de CD, significa que la aplicación recibe plena confianza. Todas las actualizaciones posteriores heredarán ese nivel de confianza.  
  
 Todas [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] las aplicaciones que usan `<deploymentProvider>` deben declarar explícitamente los permisos que necesitan en el manifiesto de aplicación, de modo que la aplicación no reciba distintos niveles de confianza en equipos diferentes.  
  
## <a name="see-also"></a>Consulte también  
 [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
