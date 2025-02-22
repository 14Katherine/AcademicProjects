# AcademicProjects
Principios SOLID
Integrantes: 
Jhon Steven Zuñiga Muñoz
Juan Esteban Mera Mera
Anyi Katherine Sánchez Yasnó

Principios SOLID violados :
1. Principio de Inversión de Dependencias	
2. Principio de Responsabilidad Única	
3. Principio de Sustitución de Liskov	
4. Principio de Segregación de Interfaces	

En qué parte se ve la flexibilidad:
Repositorios: El hecho de que CompanyArraysRepository y CompanySqliteRepository implementen la misma interfaz ICompanyRepository permite que se cambien entre sí sin necesidad de modificar otras partes del código que dependan del repositorio.
Persistencia: Gracias a la abstracción proporcionada por la interfaz, es posible cambiar el tipo de almacenamiento (de memoria a base de datos) sin tener que reescribir la lógica del negocio que utiliza estos repositorios. Si en el futuro se requiere otro tipo de base de datos, basta con crear una nueva clase que implemente ICompanyRepository sin necesidad de modificar el resto de la aplicación.

Implementación de un Repositorio en Archivo Binario de Solo Lectura
1. ¿Qué principio de diseño se estaría violando?
Se estaría violando el principio de "Responsabilidad Única" (SRP),la razón es que un repositorio de sólo lectura en un archivo binario tiene una responsabilidad diferente a la de un repositorio que permita modificaciones o adiciones de datos. Este repositorio tendría que asumir la responsabilidad de interactuar con un archivo binario y, al mismo tiempo, mantener las responsabilidades de un repositorio convencional que soporta operaciones de lectura y escritura. Esto crea un diseño que hace que la clase sea responsable de más de una cosa.


3. ¿Qué otro principio podría venir al rescate?
El Principio de Segregación de Interfaces (ISP), Para resolver esto, se podría refactorizar la interfaz ICompanyRepository en dos interfaces diferentes: una para operaciones de solo lectura (ICompanyRepositoryRead) y otra para operaciones de lectura y escritura (ICompanyRepositoryWrite). Esto aseguraría que las implementaciones de repositorios de sólo lectura no tengan que implementar métodos de escritura, y viceversa. De esta forma, las clases implementarán únicamente los métodos que realmente necesitan.



