---
title: Implementar manualmente la aplicación ClickOnce & mantener la marca
description: Aprenda a crear aplicaciones ClickOnce para que las implementen los clientes sin generar un nuevo manifiesto de implementación y que puedan usar la personalización de marca del cliente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0e8895f45524526fc8007ff909a9c541e9899b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917269"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Tutorial: implementar manualmente una aplicación ClickOnce que no requiera volver a firmar y que conserve la información de personalización de marca
Cuando se crea una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación y, a continuación, se le asigna a un cliente para que la publique e implemente, el cliente tradicionalmente ha tenido que actualizar el manifiesto de implementación y volver a firmarlo. Aunque todavía es el método preferido en la mayoría de los casos, el .NET Framework 3,5 le permite crear [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementaciones que los clientes pueden implementar sin tener que volver a generar un nuevo manifiesto de implementación. Para obtener más información, consulte [deploy ClickOnce Applications for Testing and Production Servers sin tener que volver a firmar](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

 Cuando se crea una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación y, a continuación, se le asigna a un cliente para que la publique e implemente, la aplicación puede usar la personalización de marca del cliente o puede conservar la personalización de marca. Por ejemplo, si la aplicación es una aplicación de propiedad única, es posible que desee conservar la personalización de marca. Si la aplicación es muy personalizada para cada cliente, es posible que desee usar la personalización de marca del cliente. El .NET Framework 3,5 le permite conservar su marca, la información de editor y la firma de seguridad al proporcionar una aplicación a una organización para implementar. Para obtener más información, vea [crear aplicaciones ClickOnce para que las implementen otras personas](../deployment/creating-clickonce-applications-for-others-to-deploy.md).

> [!NOTE]
> En este tutorial, creará implementaciones de forma manual mediante la herramienta de línea de comandos *Mage.exe* o la herramienta gráfica *MageUI.exe*. Para obtener más información acerca de las implementaciones manuales, vea [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="prerequisites"></a>Requisitos previos
 Para realizar los pasos de este tutorial, necesitará lo siguiente:

- Una aplicación Windows Forms que está listo para implementar. Esta aplicación se conoce como *WindowsFormsApp1*.

- Visual Studio o el Windows SDK.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Para implementar una aplicación ClickOnce con compatibilidad con varias implementaciones y personalización de marca mediante Mage.exe

1. Abra un símbolo del sistema de Visual Studio o un [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] símbolo del sistema y cambie al directorio en el que almacenará los [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos.

2. Cree un directorio con el nombre de la versión actual de la implementación. Si es la primera vez que implementa la aplicación, es probable que elija **1.0.0.0**.

   > [!NOTE]
   > La versión de la implementación puede ser distinta de la versión de los archivos de aplicación.

3. Cree un subdirectorio denominado **bin** y copie todos los archivos de aplicación aquí, incluidos los archivos ejecutables, los ensamblados, los recursos y los archivos de datos.

4. Genere el manifiesto de aplicación con una llamada a Mage.exe.

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. Firme el manifiesto de aplicación con el certificado digital.

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. Genere el manifiesto de implementación con una llamada a *Mage.exe*. De forma predeterminada, *Mage.exe* marcará la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación como una aplicación instalada, de modo que se pueda ejecutar tanto en línea como sin conexión. Para que la aplicación esté disponible solo cuando el usuario está en línea, use el `-i` argumento con un valor de `f` . Dado que esta aplicación se beneficiará de la característica de implementación múltiple, excluya el `-providerUrl` argumento para *Mage.exe*. (En las versiones de .NET Framework anteriores a la versión 3,5, excluida `-providerUrl` una aplicación sin conexión producirá un error).

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. No firme el manifiesto de implementación.

8. Proporcione todos los archivos al cliente, que implementarán la aplicación en su red.

9. En este momento, el cliente debe firmar el manifiesto de implementación con su propio certificado generado automáticamente. Por ejemplo, si el cliente trabaja para una empresa denominada Adventure Works, puede generar un certificado autofirmado mediante la herramienta *MakeCert.exe* . A continuación, use la herramienta de *Pvk2pfx.exe* para combinar los archivos creados por *MakeCert.exe* en un archivo PFX que se puede pasar a *Mage.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. El cliente siguiente utiliza este certificado para firmar el manifiesto de implementación.

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. El cliente implementa la aplicación en sus usuarios.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Para implementar una aplicación ClickOnce con compatibilidad con varias implementaciones y personalización de marca mediante MageUI.exe

1. Abra un símbolo del sistema de Visual Studio o un [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] símbolo del sistema y navegue hasta el directorio en el que almacenará los [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos.

2. Cree un subdirectorio denominado **bin** y copie todos los archivos de aplicación aquí, incluidos los archivos ejecutables, los ensamblados, los recursos y los archivos de datos.

3. Cree un subdirectorio con el nombre de la versión actual de la implementación. Si es la primera vez que implementa la aplicación, es probable que elija **1.0.0.0**.

   > [!NOTE]
   > La versión de la implementación puede ser distinta de la versión de los archivos de aplicación.

4. Mueva el \\ directorio **bin** al directorio que creó en el paso 2.

5. Inicie la herramienta gráfica *MageUI.exe*.

   ```cmd
   MageUI.exe
   ```

6. Cree un nuevo manifiesto de aplicación seleccionando **archivo**, **nuevo**, **manifiesto de aplicación** en el menú.

7. En la pestaña **nombre** predeterminado, escriba el nombre y el número de versión de esta implementación. Además, proporcione un valor para **publicador**, que se usará como nombre de carpeta para el vínculo de acceso directo de la aplicación en el menú Inicio cuando se implemente.

8. Seleccione la pestaña Opciones de la **aplicación** y haga clic en **usar el manifiesto de aplicación para obtener información de confianza**. Esto habilitará la personalización de marca de terceros para esta [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.

9. Seleccione la pestaña **archivos** y haga clic en el botón **examinar** situado junto al cuadro de texto directorio de la **aplicación** .

10. Seleccione el directorio que contiene los archivos de aplicación que creó en el paso 2 y haga clic en **Aceptar** en el cuadro de diálogo Selección de carpeta.

11. Haga clic en el botón **rellenar** para agregar todos los archivos de aplicación a la lista de archivos. Si la aplicación contiene más de un archivo ejecutable, marque el archivo ejecutable principal para esta implementación como aplicación de inicio; para ello, seleccione **punto de entrada** en la lista desplegable tipo de **archivo** . (Si la aplicación solo contiene un archivo ejecutable, *MageUI.exe* lo marcará automáticamente).

12. Seleccione la pestaña **permisos necesarios** y seleccione el nivel de confianza que necesita para la aplicación. El valor predeterminado es **plena confianza**, que será adecuado para la mayoría de las aplicaciones.

13. Seleccione **archivo**, **Guardar** en el menú y guarde el manifiesto de aplicación. Cuando lo guarde, se le pedirá que firme el manifiesto de aplicación.

14. Si tiene un certificado almacenado como un archivo en el sistema de archivos, use la opción **firmar como archivo de certificado** y seleccione el certificado en el sistema de archivos mediante el botón de puntos suspensivos (**...**).

     o bien

     Si el certificado se mantiene en un almacén de certificados al que se puede tener acceso desde el equipo, seleccione la **opción firmar con certificado almacenado** y seleccione el certificado en la lista que se proporciona.

15. Seleccione **archivo**, **nuevo**, **manifiesto de implementación** en el menú para crear el manifiesto de implementación y, a continuación, en la pestaña **nombre** , proporcione un nombre y un número de versión (**1.0.0.0** en este ejemplo).

16. Cambie a la pestaña **Actualizar** y especifique la frecuencia con la que desea que se actualice la aplicación. Si la aplicación usa la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API de implementación para buscar actualizaciones, desactive la casilla **esta aplicación debe buscar actualizaciones**.

17. Cambie a la pestaña referencia de la **aplicación** . Para rellenar previamente todos los valores de esta pestaña, haga clic en el botón **seleccionar manifiesto** y seleccione el manifiesto de aplicación que creó en pasos anteriores.

18. Elija **Guardar** y guarde el manifiesto de implementación en el disco. Cuando lo guarde, se le pedirá que firme el manifiesto de aplicación. Haga clic en **Cancelar** para guardar el manifiesto sin firmarlo.

19. Proporcione todos los archivos de aplicación al cliente.

20. En este momento, el cliente debe firmar el manifiesto de implementación con su propio certificado generado automáticamente. Por ejemplo, si el cliente trabaja para una empresa denominada Adventure Works, puede generar un certificado autofirmado mediante la herramienta *MakeCert.exe* . A continuación, use la herramienta de *Pvk2pfx.exe* para combinar los archivos creados por *MakeCert.exe* en un archivo PFX que se puede pasar a *MageUI.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. Con el certificado generado, el cliente ahora firma el manifiesto de implementación al abrir el manifiesto de implementación en *MageUI.exe* y, a continuación, guardarlo. Cuando aparece el cuadro de diálogo firma, el cliente selecciona la opción **firmar como archivo de certificado** y elige el archivo PFX que ha guardado en el disco.

22. El cliente implementa la aplicación en sus usuarios.

## <a name="see-also"></a>Vea también
- [Mage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Herramienta de generación y edición de manifiestos, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [MakeCert](/windows/desktop/SecCrypto/makecert)
