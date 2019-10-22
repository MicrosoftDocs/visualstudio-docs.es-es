---
title: Crear un instalador personalizado para la aplicación ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b648134b7ad27a8f622ce270dc0f05e0a7e6516c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637426"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Tutorial: crear un instalador personalizado para una aplicación ClickOnce
Cualquier aplicación ClickOnce basada en un archivo *. exe* se puede instalar y actualizar de forma silenciosa mediante un instalador personalizado. Un instalador personalizado puede implementar la experiencia personalizada del usuario durante la instalación, incluidos los cuadros de diálogo personalizados para las operaciones de seguridad y mantenimiento. Para realizar operaciones de instalación, el instalador personalizado utiliza la clase <xref:System.Deployment.Application.InPlaceHostingManager>. En este tutorial se muestra cómo crear un instalador personalizado que instala una aplicación ClickOnce de forma silenciosa.

## <a name="prerequisites"></a>Requisitos previos

### <a name="to-create-a-custom-clickonce-application-installer"></a>Para crear un instalador de aplicación ClickOnce personalizado

1. En la aplicación ClickOnce, agregue referencias a System. Deployment y System. Windows. Forms.

2. Agregue una nueva clase a la aplicación y especifique cualquier nombre. Este tutorial usa el nombre `MyInstaller`.

3. Agregue las siguientes directivas de `Imports` o `using` a la parte superior de la nueva clase.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Agregue los métodos siguientes a la clase.

     Estos métodos llaman a métodos de <xref:System.Deployment.Application.InPlaceHostingManager> para descargar el manifiesto de implementación, validar los permisos adecuados, solicitar al usuario permiso para instalar y, a continuación, descargar e instalar la aplicación en la caché de ClickOnce. Un instalador personalizado puede especificar que una aplicación ClickOnce es de preconfianza o puede diferir la decisión de confianza a la llamada al método <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>. Este código confía previamente en la aplicación.

    > [!NOTE]
    > Los permisos asignados por la preconfianza no pueden superar los permisos del código del instalador personalizado.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5. Para intentar la instalación desde el código, llame al método `InstallApplication`. Por ejemplo, si llama a la clase `MyInstaller`, puede llamar a `InstallApplication` de la siguiente manera.

    ```vb
    Dim installer As New MyInstaller()
    installer.InstallApplication("\\myServer\myShare\myApp.application")
    MessageBox.Show("Installer object created.")
    ```

    ```csharp
    MyInstaller installer = new MyInstaller();
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");
    MessageBox.Show("Installer object created.");
    ```

## <a name="next-steps"></a>Pasos siguientes
 Una aplicación ClickOnce también puede agregar lógica de actualización personalizada, incluida una interfaz de usuario personalizada para mostrar durante el proceso de actualización. Para obtener más información, vea <xref:System.Deployment.Application.UpdateCheckInfo>. Una aplicación ClickOnce también puede suprimir la entrada del menú Inicio estándar, el acceso directo, y agregar o quitar programas mediante un elemento `<customUX>`. Para obtener más información, vea [\<entryPoint > elemento](../deployment/entrypoint-element-clickonce-application.md) y <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.

## <a name="see-also"></a>Vea también
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<entryPoint elemento >](../deployment/entrypoint-element-clickonce-application.md)
