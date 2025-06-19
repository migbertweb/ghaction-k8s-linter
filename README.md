# ghaction-k8s-linter 🚦🔍

Workflow reutilizable para validar manifiestos de Kubernetes con [`kube-linter`](https://github.com/stackrox/kube-linter) y [`kubeconform`](https://github.com/yannh/kubeconform), con notificación automática vía Telegram.

Ideal para pipelines CI/CD que trabajen con Kustomize, Helm o YAML plano.

---

## 📦 ¿Qué hace este Action?

1. Valida recursos Kubernetes con `kube-linter` y `kubeconform`.
2. Si todo pasa ✅, envía un resumen a Telegram.
3. Si algo falla ❌, además del mensaje, adjunta los logs como `.tar.gz`.

---

## 🚀 Cómo usar

Agregá esto en tu workflow principal (`.github/workflows/ci.yml` o similar):

```yaml
jobs:
  lint:
    uses: migbert/ghaction-k8s-linter/.github/workflows/lint-k8s.yml@main
    with:
      path: "ruta/a/tus/manifiestos"
    secrets:
      TELEGRAM_BOT_TOKEN: ${{ secrets.TELEGRAM_BOT_TOKEN }}
      TELEGRAM_CHAT_ID: ${{ secrets.TELEGRAM_CHAT_ID }}
