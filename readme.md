tfmicro for esp32 from tensorflow 2.4.2 

how this was made

Clone Tensorflow
	git clone https://github.com/tensorflow/tensorflow.git
Cd tensorflow
Checkout the version you wish to build
	git fetch --all --tags
	git checkout tags/v2.4.2
tensorflow/lite/micro/tools/make/targets/esp32_makefile.inc is wrong 
	esp needs to be esp32 edit it change it
make -f tensorflow/lite/micro/tools/make/Makefile TARGET=esp32 generate_hello_world_esp_project
cd tensorflow/lite/micro/tools/make/gen/esp32_xtensa-esp32/prj/hello_world/esp-idf
idf.py build

For me the failed at the end but the tensorflow files did get created
/tensorflow/tensorflow/lite/micro/tools/make/gen/esp32_xtensa-esp32/prj/hello_world/esp-idf/components/tfmicro/

cp -r  ./third_party/flatbuffers/include/flatbuffers/ ./
cp -r ./third_party/gemmlowp/fixedpoint/ ./
cp -r ./third_party/gemmlowp/internal/ ./
cp -r ./third_party/kissfft/ ./
cp -r ./third_party/ruy/ruy/ ./

Replace floating functions

In lib\TensorflowLiteEsp32\src/tensorflow/lite/kernels/internal/min.h
Define 
#define TF_LITE_USE_GLOBAL_MIN

In lib\TensorflowLiteEsp32\src/tensorflow/lite/kernels/internal/max.h
Define 
#define TF_LITE_USE_GLOBAL_MAX
