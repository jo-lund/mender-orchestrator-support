Rtos artifacts were created with:

```bash
DEVICE=rtos
VERSION=$DEVICE-v3
PAYLOAD=$VERSION-payload

touch $PAYLOAD
mender-artifact \
  write module-image \
  --type $DEVICE \
  --device-type $DEVICE \
  --provides version:$VERSION \
  --clears-provides version.* \
  --no-default-clears-provides \
  --no-default-software-version \
  --file $PAYLOAD \
  --output-path $VERSION.mender \
  --artifact-name $VERSION
```



The manifest artifacts were created with:

``` bash
DEVICE_TYPE="qemux86-64"
./mender-orchestrator-manifest-gen \
    -n manifest-v1 \
    -o manifest-v1.mender \
    -t $DEVICE_TYPE \
    manifest-v1.yaml
```
