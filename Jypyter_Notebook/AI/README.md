# PYNQ ZU DPU Example
### Download DPU Core
>After you burn the image from the E-Elements website, you could add the dpu core and examples in the image.
```
pip3 install pynq-dpu --no-build-isolation
cd $PYNQ_JUPYTER_NOTEBOOKS
pynq get-notebooks pynq-dpu -p .
python3 -m pytest --pyargs pynq_dpu
```
> **Ref.** [DPU-PYNQ](https://github.com/Xilinx/DPU-PYNQ)
