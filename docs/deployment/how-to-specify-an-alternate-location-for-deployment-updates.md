---
title: 'Cómo: especificar una ubicación alternativa para las actualizaciones de implementación | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 76be049c670fb91911be70132b459cad5e5183bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902469"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Cómo: especificar una ubicación alternativa para las actualizaciones de implementación
Puede instalar su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación inicialmente desde un CD o un recurso compartido de archivos, pero la aplicación debe buscar actualizaciones periódicas en la Web. Puede especificar una ubicación alternativa para las actualizaciones en el manifiesto de implementación para que la aplicación pueda actualizarse desde el Web tras la instalación inicial.  
  
> [!NOTE]
>  La aplicación debe configurarse para instalar localmente para usar esta característica. Para obtener más información, consulte [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Además, si instala un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación desde la red, establecer una ubicación alternativa, se produce la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usar esa ubicación para la instalación inicial y todas las actualizaciones subsiguientes. Si instala la aplicación localmente (por ejemplo, desde un CD), la instalación inicial se realiza mediante el medio original y todas las actualizaciones subsiguientes usará la ubicación alternativa.  
  
### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Especificar una ubicación alternativa para las actualizaciones mediante MageUI.exe (Utilidad basada en formularios de Windows)  
  
1.  Abra un símbolo del sistema de .NET Framework y escriba:  
  
     **MageUI.exe**  
  
2.  En el **archivo** menú, elija **abrir** para abrir el manifiesto de implementación de la aplicación.  
  
3.  Seleccione el **opciones de implementación** ficha.  
  
4.  En el cuadro de texto denominado **iniciar ubicación**, escriba la dirección URL del directorio que contendrá el manifiesto de implementación de actualizaciones de la aplicación.  
  
5.  Guarde el manifiesto de implementación.  
  
### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Especificar una ubicación alternativa para las actualizaciones mediante Mage.exe  
  
1. Abra un símbolo del sistema de .NET Framework.  
  
2. Establezca la ubicación de actualización mediante el comando siguiente. En este ejemplo, *HelloWorld.exe.application* es la ruta de acceso a su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación, que siempre tiene la extensión .application, y *<http://adatum.com/Update/Path>* es la dirección URL que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] comprobará las actualizaciones de la aplicación.  
  
    **Mage-actualizar HelloWorld.exe.application - ProviderUrl http://adatum.com/Update/Path**  
  
3. Guarde el archivo.  
  
   > [!NOTE]
   >  Ahora debe volver a firmar el archivo con *Mage.exe*. Para obtener más información, consulte [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Si instala la aplicación desde un medio sin conexión, como un CD, y el equipo está conectado, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] comprueba primero la dirección URL especificada por el `<deploymentProvider>` etiqueta en el manifiesto de implementación para determinar si la ubicación de actualización contiene una versión más reciente de la aplicación. Si es así, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instala la aplicación directamente desde ahí, en lugar de desde el directorio de instalación inicial, y common language runtime (CLR) determina la confianza de la aplicación con el nivel `<deploymentProvider>`. Si el equipo está sin conexión, o `<deploymentProvider>` es inaccesible, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalaciones desde el CD y CLR concede confianza según el punto de instalación; para realizar una instalación de CD, esto significa que la aplicación reciba plena confianza. Todas las actualizaciones subsiguientes heredarán ese nivel de confianza.  
  
 Todos los [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones que usan `<deploymentProvider>` debe declarar explícitamente los permisos que necesitan en el manifiesto de aplicación para que la aplicación no recibe los diferentes niveles de confianza en equipos diferentes.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)