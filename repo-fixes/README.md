# Arreglos para los repos públicos

Desde la sesión en la nube no pude hacer push a estos repos ni editar sus descripciones (la app de Claude solo tiene acceso a `GabAntoLocia/GabAntoLocia`). Aquí están listos para aplicar desde tu PC.

## 1. Parches de README

```bash
# motor: README en UTF-8 (antes estaba en UTF-16 y GitHub lo mostraba roto),
#        motor.js con module.exports (npm start fallaba en Node < 22.12)
#        y descripción de package.json limpia
cd motor && git apply ../GabAntoLocia/repo-fixes/motor/fix.patch \
  && git commit -am "Fix README encoding, CommonJS export and package description" && git push

# file-management-api: reemplaza la plantilla de NestJS por un README real
cd file-management-api && git apply ../GabAntoLocia/repo-fixes/file-management-api/fix.patch \
  && git commit -am "Replace NestJS boilerplate README" && git push
```

> `file-management-api` no compila: `AppModule` importa `src/auth`, `src/users` y `src/files`, que nunca se subieron. Súbelos si los tienes en tu PC. Si no, conviene archivar el repo o hacerlo privado.

## 2. Descripciones y topics (gh CLI)

```bash
gh repo edit GabAntoLocia/backend-patterns-showcase -d "Reference Node.js/TypeScript backend: hexagonal architecture, HMAC webhooks, idempotent queue, magic-link auth. Zero external deps, 51 tests." --add-topic typescript,nodejs,hexagonal-architecture,clean-architecture,vitest
gh repo edit GabAntoLocia/historiBot -d "Asistente de historia universal con voz y LLM conversacional. Monorepo TypeScript + Vue 3." --add-topic typescript,vue,llm,web-speech-api
gh repo edit GabAntoLocia/academic_grades -d "API REST de gestión de notas con Django REST Framework, DDD y JWT." --add-topic python,django,ddd,jwt
gh repo edit GabAntoLocia/task-manager-services -d "API Gateway + microservicios (usuarios y tareas) con NestJS, Prisma, PostgreSQL y Docker." --add-topic nestjs,microservices,prisma,docker
gh repo edit GabAntoLocia/easybroker_client -d "Cliente Ruby para la API de EasyBroker: lista propiedades de la cuenta de staging." --add-topic ruby,api-client
gh repo edit GabAntoLocia/motor -d "Motor de decisión de crédito en Node.js que genera un reporte en PDF (PDFKit)." --add-topic nodejs,pdfkit
gh repo edit GabAntoLocia/file-management-api -d "API de gestión de archivos con NestJS y MongoDB (en construcción)." --add-topic nestjs,mongodb
gh repo edit GabAntoLocia/CV -d "CV de Gabriel Antaño Locia (PDF)."
gh repo edit GabAntoLocia/GabAntoLocia.github.io -d "Portafolio — Gabriel Antaño Locia" --homepage https://gabantolocia.github.io
```
