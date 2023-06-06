### cflinuxfs4-compat BOSH Release

This repository is a [BOSH](https://github.com/cloudfoundry/bosh) release for
deploying the cflinuxfs4 rootfs (with the addition of ruby, python, and associated packages)
package as well as a job that will extract the package to
`/var/vcap/packages/cflinuxfs4-compat/rootfs`.

#### Trusted certificates

Trusted certs can be installed in the rootfs by setting the
`cflinuxfs4-compat-rootfs.trusted_certs` property to the certificate chain in any
order. For example in your deployment manifest:

```
properties:
  cflinuxfs4-compat-rootfs:
    trusted_certs: |+
      -----BEGIN CERTIFICATE-----
      MIIDQjCCAiqgAwIBAgIJAP/z/IO9Vh6HMA0GCSqGSIb3DQEBBQUAMEUxCzAJBgNV
      BAYTAkFVMRMwEQYDVQQIEwpTb21lLVN0YXRlMSEwHwYDVQQKExhJbnRlcm5ldCBX
      aWRnaXRzIFB0eSBMdGQwIBcNMTYwMzAxMTg0NzQ3WhgPMjI4OTEyMTQxODQ3NDda
      MEwxCzAJBgNVBAYTAlVTMRUwEwYDVQQKEwxDTE9VREZPVU5EUlkxJjAkBgNVBAMT
      HWJsb2JzdG9yZS5zZXJ2aWNlLmNmLmludGVybmFsMIIBIjANBgkqhkiG9w0BAQEF
      AAOCAQ8AMIIBCgKCAQEAmcQD0ryug94fllXGM9+mpfHTrT++ZTGZpZ0KCde0iky7
      fprXiVIoHMqgCDnPvSmI7AUZ0TIxYZtm9FfIkdtjk0QW8PbXmbxEBQwH75EgPqNS
      0rkkmwzvVlPI963CTyR0SNpjK8s5GpGO9PQd/OY2AQG1ty1jE1T0YLGdaI2LWsHq
      Y11WFkPYdOfYVnSZeiJkvOkZdZ5KQjZLfgMtyg3cV7yIA552OQiQn3OAFl15K0Bg
      XTjHWfgu5vVGDr/dw0/Dlm2M56EIRBvc/XBJ9/+cj++R3ru77EfJF/h5vn1ahSxZ
      RLWOmDoEOhfDmZ9w/QNWFpHWGJ9dHH7wLN8W/naUkwIDAQABoywwKjAoBgNVHREE
      ITAfgh1ibG9ic3RvcmUuc2VydmljZS5jZi5pbnRlcm5hbDANBgkqhkiG9w0BAQUF
      AAOCAQEABHHiEQW+lG2kM987QeRkycXAwASUtZJV8wrbB8PUn9BC799TVXGkpFLr
      oflUnw4hxAlnwrSYWX+1ueCJ2cR1HoXUMTrwK4a5GUtoHnKJQwnb8K+z7lC+0oqE
      GX+CTb7pPjxwHKGgRw1jjRNLaf3wxnSMrS73OcikF5aGcHylxdCDhAMDvcX6xuqP
      kDMh20Kjg5brpRhZdkBIe9Tja8W4MZfugzZrPamvo14mRinZVnpiXodvhGHxkHvZ
      /SA6HwVuqxoYEC+lqJkLbSqyVPSxLvidKl1Zb6074AZxmVlipmrnEETLaScE98Fp
      XqP9Bw730tiw8W3mZ3NFDQtwAowlqw==
      -----END CERTIFICATE-----
```


#### Running smoke tests

1. Target your bosh director

1. Run `bosh -n deploy -d rootfs-smoke-test manifests/manifest.yml && bosh run-errand -d rootfs-smoke-test cflinuxfs4-compat-smoke-test`

