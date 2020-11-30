---
title: Procedimientos recomendados para usar fragmentos de código
description: Aprenda sobre los fragmentos de código, la intención de un fragmento de código y el mejor modo de usarlos para que se adapten a su aplicación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f54a451bea8345d06073e6f3a8ab944b3c7ea820
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903148"
---
# <a name="best-practices-for-using-code-snippets"></a>Procedimientos recomendados para usar fragmentos de código

El código de un fragmento de código muestra solo la forma más sencilla de hacer algo. Para la mayoría de las aplicaciones, el código debe modificarse para adaptarlo a la aplicación.

## <a name="handling-exceptions"></a>Control de excepciones

Normalmente, el fragmento de código Try...Catch bloquea catch y vuelve a iniciar todas las excepciones. Es posible que esta no sea la elección correcta para su proyecto. Para cada excepción, hay varias formas de responder. Para obtener ejemplos, vea [Cómo: Controlar una excepción mediante Try y Catch (Guía de programación de C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) e [Instrucción Try...Catch...Finally (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Ubicaciones de archivo

Al adaptar las ubicaciones de archivo a la aplicación, debe tener en cuenta lo siguiente:

- Encontrar una ubicación accesible. Es posible que los usuarios no tengan acceso a la carpeta *Archivos de programa* del equipo, por lo que puede que no sirva almacenar archivos con los archivos de aplicación.

- Encontrar una ubicación segura. Almacenar archivos en la carpeta raíz (*C:\\* ) no es seguro. Para los datos de aplicaciones, le recomendamos la carpeta *Application Data*. Para los datos de usuarios individuales, la aplicación puede crear un archivo para cada usuario en la carpeta *Documentos*.

- Usar un nombre de archivo válido. Puede usar los controles <xref:System.Windows.Forms.OpenFileDialog> y <xref:System.Windows.Forms.SaveFileDialog> para reducir la probabilidad de nombres de archivo no válidos. Tenga en cuenta que, entre el momento en que el usuario selecciona un archivo y el tiempo que el código manipula el archivo, se puede eliminar el archivo. Además, es posible que el usuario no tenga permisos para escribir en el archivo.

## <a name="security"></a>Seguridad

El nivel de seguridad de un fragmento de código depende de dónde se usa en el código fuente y cómo se modifica una vez que está en el código. La lista siguiente contiene algunas de las áreas que deben tenerse en cuenta.

- Acceso de base de datos y archivo

- Seguridad de acceso del código

- Protección de recursos (como registros de eventos, Registro)

- Almacenamiento de secretos

- Comprobación de entradas

- Paso de datos a tecnologías de scripting

Para obtener más información, consulte [Proteger aplicaciones](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>Fragmentos de código descargados

Los fragmentos de código de IntelliSense instalados por Visual Studio no constituyen por sí mismos un peligro para la seguridad. En cambio, pueden crear riesgos de seguridad en la aplicación. Los fragmentos de código descargados de Internet deben tratarse como cualquier otro contenido descargado: con extrema precaución.

- Descargue fragmentos solo de sitios de confianza y use software antivirus actualizado.

- Abra todos los archivos de fragmento de código descargados en el Bloc de notas o el editor XML de Visual Studio y examínelos detenidamente antes de instalarlos. Busque los siguientes problemas:

  - El fragmento de código podría dañar el sistema si lo ejecuta. Lea detenidamente el código fuente antes de ejecutarlo.

  - El bloque Dirección URL de ayuda del archivo de fragmento de código puede contener direcciones URL que ejecuten un archivo de script malintencionado o muestren un sitio web ofensivo.

  - El fragmento de código puede contener referencias que se agregan automáticamente al proyecto y es posible que se carguen desde cualquier lugar del sistema. Es posible que estas referencias se hayan descargado en el equipo desde el mismo sitio del que ha descargado el fragmento de código. El fragmento de código puede realizar una llamada a un método en la referencia que ejecuta código malintencionado. Para protegerse contra este tipo de ataque, revise los bloques Importaciones y Referencias del archivo de fragmentos.

## <a name="see-also"></a>Consulte también

- [Fragmentos de código de IntelliSense de Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Protección de aplicaciones](../ide/securing-applications.md)
- [Fragmentos de código](../ide/code-snippets.md)
