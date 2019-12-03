---
title: Implementar componentes COM con ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6c83367881b7ed6a69fe10af8b7c68eb1692e3e6
ms.sourcegitcommit: 49ebf69986713e440fd138fb949f1c0f47223f23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74706892"
---
# <a name="deploying-com-components-with-clickonce"></a>Implementar componentes COM con ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La implementación de componentes COM heredados tradicionalmente ha sido una tarea difícil. Los componentes deben estar registrados globalmente y, por tanto, pueden producir efectos secundarios no deseados entre las aplicaciones superpuestas. Normalmente, esta situación no es un problema en .NET Framework aplicaciones porque los componentes están completamente aislados en una aplicación o son compatibles en paralelo. Visual Studio le permite implementar componentes COM aislados en el sistema operativo Windows XP o posterior.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] proporciona un mecanismo fácil y seguro para implementar aplicaciones .NET. Sin embargo, si las aplicaciones usan componentes COM heredados, tendrá que realizar pasos adicionales para implementarlos. En este tema se describe cómo implementar componentes COM aislados y hacer referencia a componentes nativos (por ejemplo, desde Visual Basic C++6,0 o visual).  
  
 Para obtener más información sobre la implementación de componentes COM aislados, consulte [simplificación de la implementación de aplicaciones con ClickOnce y com sin registro](/archive/msdn-magazine/2005/april/simplify-app-deployment-with-clickonce-and-registration-free-com).  
  
## <a name="registration-free-com"></a>COM sin registro  
 El COM sin registro es una nueva tecnología para implementar y activar componentes COM aislados. Funciona colocando toda la información de registro y de biblioteca de tipos del componente que normalmente se instala en el registro del sistema en un archivo XML denominado manifiesto, almacenado en la misma carpeta que la aplicación.  
  
 Aislar un componente COM requiere que se registre en el equipo del desarrollador, pero no es necesario que esté registrado en el equipo del usuario final. Para aislar un componente COM, lo único que debe hacer es establecer su propiedad **aislada** de referencia en **true**. De forma predeterminada, esta propiedad se establece en **false**, lo que indica que se debe tratar como una referencia com registrada. Si esta propiedad es **true**, hace que se genere un manifiesto para este componente en tiempo de compilación. También hace que los archivos correspondientes se copien en la carpeta de la aplicación durante la instalación.  
  
 Cuando el generador de manifiestos encuentra una referencia COM aislada, enumera todas las entradas de `CoClass` en la biblioteca de tipos del componente, que coincide con cada entrada con sus datos de registro correspondientes y genera definiciones de manifiesto para todas las clases COM en el archivo de biblioteca de tipos.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>Implementación de componentes COM sin registro mediante ClickOnce  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tecnología de implementación es idónea para implementar componentes COM aislados, ya que tanto el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] como el COM sin registro requieren que un componente tenga un manifiesto para su implementación.  
  
 Normalmente, el autor del componente debe proporcionar un manifiesto. Sin embargo, si no es así, Visual Studio es capaz de generar un manifiesto automáticamente para un componente COM. La generación del manifiesto se realiza durante el proceso de publicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]; para obtener más información, vea [publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md). Esta característica también le permite aprovechar los componentes heredados que creó en entornos de desarrollo anteriores como Visual Basic 6,0.  
  
 Hay dos maneras en las que [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementa los componentes COM:  
  
- Usar el programa previo para implementar los componentes COM; Esto funciona en todas las plataformas admitidas.  
  
- Use la implementación de aislamiento de componentes nativos (también conocida como COM sin registro). Sin embargo, esto solo funcionará en un sistema operativo Windows XP o posterior.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Ejemplo de aislamiento e implementación de un componente COM simple  
 Para demostrar la implementación de componentes COM sin registro, en este ejemplo se creará una aplicación basada en Windows en Visual Basic que hace referencia a un componente COM nativo aislado creado con Visual Basic 6,0 e implementarlo mediante [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
 En primer lugar, debe crear el componente COM nativo:  
  
##### <a name="to-create-a-native-com-component"></a>Para crear un componente COM nativo  
  
1. Con Visual Basic 6,0, en el menú **archivo** , haga clic en **nuevo**y luego en **proyecto**.  
  
2. En el cuadro de diálogo **nuevo proyecto** , seleccione el nodo **Visual Basic** y seleccione un proyecto **dll de ActiveX** . En el cuadro **Nombre** , escriba `VB6Hello`.  
  
    > [!NOTE]
    > El archivo DLL de ActiveX y los tipos de proyecto de control ActiveX solo se admiten con COM sin registro; No se admiten los tipos de proyecto ActiveX EXE y documentos ActiveX.  
  
3. En **Explorador de soluciones**, haga doble clic en **Class1. VB** para abrir el editor de texto.  
  
4. En Class1. VB, agregue el código siguiente después del código generado para el método `New`:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5. Compile el componente. En el menú **compilar** , haga clic en **compilar solución**.  
  
> [!NOTE]
> El COM sin registro solo admite los tipos de proyecto archivos dll y controles COM. No se puede utilizar exe con COM sin registro.  
  
 Ahora puede crear una aplicación basada en Windows y agregarle una referencia al componente COM.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Para crear una aplicación basada en Windows mediante un componente COM  
  
1. Con Visual Basic, en el menú **archivo** , haga clic en **nuevo**y luego en **proyecto**.  
  
2. En el cuadro de diálogo **nuevo proyecto** , seleccione el nodo **Visual Basic** y seleccione **aplicación para Windows**. En el cuadro **Nombre** , escriba `RegFreeComDemo`.  
  
3. En **Explorador de soluciones**, haga clic en el botón **Mostrar todos los archivos** para mostrar las referencias del proyecto.  
  
4. Haga clic con el botón secundario en el nodo **referencias** y seleccione **Agregar referencia** en el menú contextual.  
  
5. En el cuadro de diálogo **Agregar referencia** , haga clic en la pestaña **examinar** , vaya a VB6Hello. dll y, a continuación, selecciónelo.  
  
    Aparece una referencia de **VB6Hello** en la lista de referencias.  
  
6. Seleccione el **cuadro de herramientas**, seleccione un control de **botón** y arrástrelo al formulario **Form1** .  
  
7. En la ventana **propiedades** , establezca la propiedad **texto** del botón en **Hello**.  
  
8. Haga doble clic en el botón para agregar el código del controlador y, en el archivo de código, agregue el código para que el controlador Lea de la siguiente manera:  
  
   ```  
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim VbObj As New VB6Hello.Class1  
       VbObj.SayHello()  
   End Sub  
   ```  
  
9. Ejecute la aplicación. En el menú **depurar** , haga clic en **iniciar depuración**.  
  
   A continuación, debe aislar el control. Cada componente COM que utiliza la aplicación se representa en el proyecto como una referencia COM. Estas referencias están visibles en el nodo **referencias** de la ventana **Explorador de soluciones** . (Tenga en cuenta que puede Agregar referencias directamente mediante el comando **Agregar referencia** en el menú **proyecto** o directamente arrastrando un control ActiveX al formulario).  
  
   En los pasos siguientes se muestra cómo aislar el componente COM y publicar la aplicación actualizada que contiene el control aislado:  
  
##### <a name="to-isolate-a-com-component"></a>Para aislar un componente COM  
  
1. En **Explorador de soluciones**, en el nodo **referencias** , seleccione la referencia **VB6Hello** .  
  
2. En la ventana **propiedades** , cambie el valor de la propiedad **aislada** de **false** a **true**.  
  
3. En el menú **compilar** , haga clic en **compilar solución**.  
  
   Ahora, cuando presiona F5, la aplicación funciona según lo previsto, pero ahora se está ejecutando en COM sin registro. Para demostrar esto, intente anular el registro del componente VB6Hello. dll y ejecutar RegFreeComDemo1. exe fuera del IDE de Visual Studio. Esta vez, cuando se hace clic en el botón, sigue funcionando. Si cambia temporalmente el nombre del manifiesto de aplicación, se producirá un error.  
  
> [!NOTE]
> Puede simular la ausencia de un componente COM anulando su registro temporalmente. Abra un símbolo del sistema, vaya a la carpeta del sistema escribiendo `cd /d %windir%\system32`y, a continuación, anule el registro del componente escribiendo `regsvr32 /u VB6Hello.dll`. Para volver a registrarla, escriba `regsvr32 VB6Hello.dll`.  
  
 El paso final consiste en publicar la aplicación mediante [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Para publicar una actualización de la aplicación con un componente COM aislado  
  
1. En el menú **compilar** , haga clic en **publicar RegFreeComDemo**.  
  
    Aparece el Asistente de publicación.  
  
2. En el Asistente para publicación, especifique una ubicación en el disco del equipo local a la que pueda obtener acceso y examine los archivos publicados.  
  
3. Haga clic en **Finalizar** para publicar la aplicación.  
  
   Si examina los archivos publicados, observará que el archivo Sysmon. ocx está incluido. El control está totalmente aislado de esta aplicación, lo que significa que si el equipo del usuario final tiene otra aplicación que usa una versión diferente del control, no puede interferir con esta aplicación.  
  
## <a name="referencing-native-assemblies"></a>Hacer referencia a ensamblados nativos  
 Visual Studio admite referencias a ensamblados Visual Basic 6,0 C++ o nativos. dichas referencias se denominan referencias nativas. Puede saber si una referencia es nativa comprobando que su propiedad **tipo de archivo** está establecida en **nativo** o **ActiveX**.  
  
 Para agregar una referencia nativa, use el comando **Agregar referencia** y busque el manifiesto. Algunos componentes colocan el manifiesto dentro del archivo DLL. En este caso, puede elegir simplemente el propio archivo DLL y Visual Studio lo agregará como una referencia nativa si detecta que el componente contiene un manifiesto incrustado. Visual Studio también incluirá automáticamente los archivos o ensamblados dependientes que se enumeran en el manifiesto si están en la misma carpeta que el componente al que se hace referencia.  
  
 El aislamiento de controles COM facilita la implementación de componentes COM que aún no tienen manifiestos. Sin embargo, si se proporciona un componente con un manifiesto, puede hacer referencia al manifiesto directamente. De hecho, siempre debe usar el manifiesto proporcionado por el autor del componente siempre que sea posible, en lugar de usar la propiedad **aislada** .  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Limitaciones de la implementación de componentes COM sin registro  
 El COM sin registro ofrece ventajas claras sobre las técnicas de implementación tradicionales. Sin embargo, hay algunas limitaciones y advertencias que también se deben señalar. La mayor limitación es que solo funciona en Windows XP o posterior. La implementación de COM sin registro requiere cambios en la forma en que se cargan los componentes en el sistema operativo principal. Desafortunadamente, no hay ninguna capa de soporte de nivel inferior para COM sin registro.  
  
 No todos los componentes son un candidato adecuado para COM sin registro. Un componente no es adecuado si se cumple alguna de las siguientes condiciones:  
  
- El componente es un servidor fuera de proceso. No se admiten servidores EXE; solo se admiten archivos dll.  
  
- El componente forma parte del sistema operativo o es un componente del sistema, como XML, Internet Explorer o Microsoft Data Access Components (MDAC). Debe seguir la Directiva de redistribución del autor del componente; Consulte con su proveedor.  
  
- El componente es parte de una aplicación, como Microsoft Office. Por ejemplo, no debe intentar aislar el modelo de objetos de Microsoft Excel. Esto forma parte de Office y solo se puede usar en un equipo con el producto de Office completo instalado.  
  
- El componente está pensado para usarse como complemento o como complemento, por ejemplo, un complemento de Office o un control en un explorador Web. Estos componentes normalmente requieren algún tipo de esquema de registro definido por el entorno de hospedaje que está fuera del ámbito del propio manifiesto.  
  
- El componente administra un dispositivo físico o virtual para el sistema, por ejemplo, un controlador de dispositivo para un administrador de trabajos de impresión.  
  
- El componente es un redistribuible de acceso a datos. Normalmente, las aplicaciones de datos requieren la instalación de un redistribuible de acceso a datos independiente para poder ejecutarse. No debe intentar aislar componentes como Microsoft ADO Data control, Microsoft OLE DB o Microsoft Data Access Components (MDAC). En su lugar, si la aplicación usa MDAC o SQL Server Express, debe establecerlos como requisitos previos; vea [Cómo: instalar requisitos previos con una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
  En algunos casos, es posible que el desarrollador del componente lo rediseñe para COM sin registro. Si esto no es posible, todavía puede compilar y publicar aplicaciones que dependen de ellas a través del esquema de registro estándar mediante el programa previo. Para obtener más información, vea [crear paquetes de programa previo](../deployment/creating-bootstrapper-packages.md).  
  
  Un componente COM solo se puede aislar una vez por aplicación. Por ejemplo, no se puede aislar el mismo componente COM de dos proyectos de **biblioteca de clases** diferentes que formen parte de la misma aplicación. Si lo hace, se producirá una advertencia de compilación y la aplicación no se cargará en tiempo de ejecución. Para evitar este problema, Microsoft recomienda encapsular componentes COM en una biblioteca de clases única.  
  
  Hay varios escenarios en los que es necesario el registro COM en el equipo del desarrollador, aunque la implementación de la aplicación no requiere registro. La propiedad `Isolated` requiere que el componente COM esté registrado en el equipo del desarrollador para generar automáticamente el manifiesto durante la compilación. No hay funcionalidades de captura de registros que invoquen el registro automático durante la compilación. Además, las clases no definidas explícitamente en la biblioteca de tipos no se reflejarán en el manifiesto. Cuando se usa un componente COM con un manifiesto preexistente, como una referencia nativa, es posible que no sea necesario registrar el componente en tiempo de desarrollo. Sin embargo, el registro es necesario si el componente es un control ActiveX y desea incluirlo en el **cuadro de herramientas** y en el diseñador de Windows Forms.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)
