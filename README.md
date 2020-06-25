**1. Run Python script in Slicer without GUI on a remote server** (Ubuntu 18):

```sh
    sudo apt install xvfb
    xvfb-run -a ./Slicer --no-splash --python-script ~/your_script.py
```
    
**2. Match segmentation and volume geometries** (with loading & saving data):

```python
    loadedVolumeNode = slicer.util.loadVolume(ct_path)
    loadedSegmentationNode = slicer.util.loadSegmentation(seg_path)
    loadedSegmentationNode.SetReferenceImageGeometryParameterFromVolumeNode(loadedVolumeNode)
    slicer.util.saveNode(loadedSegmentationNode, seg_path)
    slicer.mrmlScene.RemoveNode(loadedVolumeNode)
    slicer.mrmlScene.RemoveNode(loadedSegmentationNode)
```
