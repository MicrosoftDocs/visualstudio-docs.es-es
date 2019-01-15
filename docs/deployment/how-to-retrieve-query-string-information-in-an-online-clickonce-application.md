---
title: Procedimiento Recuperar información de la cadena de consulta en una aplicación ClickOnce en línea | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ff97e72342e8026cddfe80d383c07ab99e3bc99a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951019"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Procedimiento Recuperación de información de la cadena de consulta de una aplicación ClickOnce en línea
La *cadena de consulta* es la parte de una dirección URL que empieza con un signo de interrogación de cierre (?) y que contiene información arbitraria con el formato *nombre=valor*. Supongamos que tiene una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] denominada `WindowsApp1` que hospeda en `servername`, y quiere pasar un valor para la variable `username` cuando se inicia la aplicación. La dirección URL podría tener el aspecto siguiente:  
  
 `http://servername/WindowsApp1.application?username=joeuser`  
  
 Los dos procedimientos siguientes muestran cómo usar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para obtener información de la cadena de consulta.  
  
> [!NOTE]
>  Solo puede pasar información en una cadena de consulta cuando la aplicación se inicia mediante HTTP, en lugar de un recurso compartido de archivos o el sistema de archivos local.  
  
 En el primer procedimiento se muestra cómo la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] puede usar un fragmento de código para leer estos valores cuando se inicia la aplicación.  
  
 En el siguiente procedimiento se muestra cómo se configura la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mediante MageUI.exe para que pueda aceptar parámetros de cadena de consulta. Debe hacerlo siempre que publique la aplicación.  
  
> [!NOTE]
>  Antes de tomar la decisión de habilitar esta característica, consulte la sección "Seguridad" más adelante en este tema.  
  
 Para obtener información sobre cómo crear un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación mediante *Mage.exe* o *MageUI.exe*, consulte [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
> [!NOTE]
>  A partir de .NET Framework 3.5 SP1, es posible pasar argumentos de línea de comandos a una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sin conexión. Si quiere proporcionar argumentos a la aplicación, puede pasar parámetros al archivo de acceso directo con la extensión .APPREF-MS.  
  
### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Para obtener información de la cadena de consulta de una aplicación ClickOnce  
  
1.  Coloque el código siguiente en su proyecto. Para que este código funcione, deberá tener una referencia a System.Web y agregar instrucciones `using` o `Imports` para System.Web, System.Collections.Specialized y System.Deployment.Application.  
  
     [!code-csharp[ClickOnceQueryString#1](../deployment/codesnippet/CSharp/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.cs)]
     [!code-vb[ClickOnceQueryString#1](../deployment/codesnippet/VisualBasic/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.vb)]  
  
2.  Llame a la función definida previamente para recuperar una propiedad <xref:System.Collections.DictionaryBase.Dictionary%2A> de los parámetros de cadena de consulta, indexados por nombre.  
  
### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Para habilitar que se pase una cadena de consulta en una aplicación ClickOnce con MageUI.exe  
  
1. Abra el símbolo del sistema de .NET y escriba:  
  
   ```cmd  
   MageUI  
   ```  
  
2. En el menú **Archivo** , seleccione **Abrir**y abra el manifiesto de implementación para su aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , que es el archivo que acaba con la extensión `.application` .  
  
3. Seleccione el panel **Opciones de implementación** en la ventana de navegación de la izquierda y active la casilla **Permitir que se pasen los parámetros de la dirección URL a la aplicación** .  
  
4. En el menú **Archivo** , seleccione **Guardar**.  
  
> [!NOTE]
>  También puede habilitar que se pase una cadena de consulta en [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Active la casilla **Permitir que se pasen los parámetros de la dirección URL a la aplicación** . Para ello, abra **Propiedades del proyecto**, seleccione la pestaña **Publicar** , haga clic en el botón **Opciones** y, después, seleccione **Manifiestos**.  
  
## <a name="robust-programming"></a>Programación sólida  
 Cuando se usan parámetros de cadena de consulta, debe prestar mucha atención a cómo se instala y se activa la aplicación. Si la aplicación está configurada para instalarse en el equipo del usuario desde Internet o desde un recurso compartido de red, es probable que el usuario active la aplicación una sola vez a través de la dirección URL. Después de eso, el usuario normalmente activará la aplicación mediante el acceso directo del menú **Inicio** . Como resultado, se garantiza que la aplicación recibe argumentos de cadena de consulta una sola vez durante su vigencia. Si decide almacenar estos argumentos en el equipo del usuario para un uso futuro, es usted el responsable de almacenarlos de forma segura.  
  
 Si la aplicación solo está en línea, siempre se activará a través de una dirección URL. Pero, incluso en este caso, la aplicación debe escribirse de modo que funcione correctamente si faltan parámetros de cadena de consulta o si están dañados.  
  
## <a name="net-framework-security"></a>seguridad en .NET Framework  
 Permita que se pasen parámetros de la dirección URL a la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] únicamente si prevé limpiar los posibles caracteres malintencionados de la entrada antes de usarla. Las cadenas en las que haya incrustadas, por ejemplo, comillas, barras o caracteres de punto y coma pueden realizar operaciones de datos arbitrarios si se usan sin filtrar en una consulta SQL en una base de datos. Para más información sobre la seguridad de las cadenas de consulta, vea [Script Exploits Overview](https://msdn.microsoft.com/Library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).  
  
## <a name="see-also"></a>Vea también  
 [Proteger aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)