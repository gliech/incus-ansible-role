# 1.0.0 (2024-04-01)


### Features

* initial commit ([8c20c1e](https://github.com/gliech/incus-ansible-role/commit/8c20c1e345bcec99d00267961694f2dd355fa050))
* lxd_client_cert directory ([6f5b3f1](https://github.com/gliech/incus-ansible-role/commit/6f5b3f110fa8662f58d2122d679afcb810e56071))
* rewrite role to use incus ([8f7114f](https://github.com/gliech/incus-ansible-role/commit/8f7114f03bef8349806911a739210ad8a7fb59bc))


### Bug Fixes

* **defaults:** remove default for lxd_config as there is not a sensible scenario where you would not want to customize this ([b4369c6](https://github.com/gliech/incus-ansible-role/commit/b4369c6cddc6c5c1cc6435d1cfec62376858ce4d))
* filter lxd config with jq to exclude volatile values ([7144f99](https://github.com/gliech/incus-ansible-role/commit/7144f9925833836add76b12b1dd87402b33873c8))
* new lxd features networks.zones and storage.buckets in default and molecule configs ([10272d9](https://github.com/gliech/incus-ansible-role/commit/10272d967222dd127bf102b6c80353e76d0b1e37))
* remove unneeded dependency on jq as `lxd init --dump` does not expose volatile configs anymore ([5019fa4](https://github.com/gliech/incus-ansible-role/commit/5019fa42482052ad8d87ee06de596edc5a71f58c))
* revert 6f5b3f1 ([8091376](https://github.com/gliech/incus-ansible-role/commit/80913764c7b440837fabab58a4c13dd4a4c93703))
* switch license to gpl ([0651787](https://github.com/gliech/incus-ansible-role/commit/0651787716375c8f82be5dc025c605531ed4002a))


### Documentation

* README file ([fce020d](https://github.com/gliech/incus-ansible-role/commit/fce020da6b8dfc942c959780d0eec2f42a5c36ee))


### Styles

* **readme:** unintentional single quotes in readme title from role skeleton ([a6a3ce6](https://github.com/gliech/incus-ansible-role/commit/a6a3ce6f38efd4c62612fdb6bf4a9ea15d6d05e4))


### Tests

* **molecule:** remove verify step ([41f7f1f](https://github.com/gliech/incus-ansible-role/commit/41f7f1f17e4a552fade00665b0ab15238b543ecc))
* **molecule:** update lxd config in test playbook to achieve idempotency ([61e9cf4](https://github.com/gliech/incus-ansible-role/commit/61e9cf40a158b314c875d358a73cff67777bbb53))


### Continuous Integration

* **fix:** install ansible-galaxy dependencies globally ([f063d00](https://github.com/gliech/incus-ansible-role/commit/f063d0089911b8e743da8e609aa881afe1c7a1a0))
* use mose recent pipeline version ([dbabec4](https://github.com/gliech/incus-ansible-role/commit/dbabec432703d872f687b0049012c4874be88ef4))


### BREAKING CHANGES

* rewrite role to use incus
* **defaults:** remove default for lxd_config as there is not a sensible scenario where you would not want to customize this
* filter lxd config with jq to exclude volatile values
