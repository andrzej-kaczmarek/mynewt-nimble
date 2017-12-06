AR := arm-none-eabi-ar
CC := arm-none-eabi-gcc

PROJ_ROOT := ../..
NRF5_SDK_ROOT ?= ./nrf5_sdk

OBJS := \
	./src/os_port.o \
	./src/hci_transport.o \
	$(PROJ_ROOT)/porting/common/src/nimble_port.o \
	$(PROJ_ROOT)/porting/common/src/mem/mem.o \
	$(PROJ_ROOT)/porting/common/src/os/endian.o \
	$(PROJ_ROOT)/porting/common/src/os/os_mbuf.o \
	$(PROJ_ROOT)/porting/common/src/os/os_mempool.o \
	$(PROJ_ROOT)/porting/common/src/os/os_msys_init.o \
	$(PROJ_ROOT)/porting/common/src/sysinit/sysinit.o \
	$(PROJ_ROOT)/nimble/host/src/ble_att_clt.o \
	$(PROJ_ROOT)/nimble/host/src/ble_att_cmd.o \
	$(PROJ_ROOT)/nimble/host/src/ble_att.o \
	$(PROJ_ROOT)/nimble/host/src/ble_att_svr.o \
	$(PROJ_ROOT)/nimble/host/src/ble_eddystone.o \
	$(PROJ_ROOT)/nimble/host/src/ble_gap.o \
	$(PROJ_ROOT)/nimble/host/src/ble_gattc.o \
	$(PROJ_ROOT)/nimble/host/src/ble_gatts_lcl.o \
	$(PROJ_ROOT)/nimble/host/src/ble_gatts.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_adv.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_atomic.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_cfg.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_conn.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_dbg.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_hci_cmd.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_hci_evt.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_hci.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_hci_util.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_id.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_log.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_mbuf.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_misc.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_pvcy.o \
	$(PROJ_ROOT)/nimble/host/src/ble_hs_startup.o \
	$(PROJ_ROOT)/nimble/host/src/ble_ibeacon.o \
	$(PROJ_ROOT)/nimble/host/src/ble_l2cap_coc.o \
	$(PROJ_ROOT)/nimble/host/src/ble_l2cap.o \
	$(PROJ_ROOT)/nimble/host/src/ble_l2cap_sig_cmd.o \
	$(PROJ_ROOT)/nimble/host/src/ble_l2cap_sig.o \
	$(PROJ_ROOT)/nimble/host/src/ble_monitor.o \
	$(PROJ_ROOT)/nimble/host/src/ble_sm_alg.o \
	$(PROJ_ROOT)/nimble/host/src/ble_sm_cmd.o \
	$(PROJ_ROOT)/nimble/host/src/ble_sm_lgcy.o \
	$(PROJ_ROOT)/nimble/host/src/ble_sm.o \
	$(PROJ_ROOT)/nimble/host/src/ble_sm_sc.o \
	$(PROJ_ROOT)/nimble/host/src/ble_store.o \
	$(PROJ_ROOT)/nimble/host/src/ble_store_util.o \
	$(PROJ_ROOT)/nimble/host/src/ble_uuid.o \
	$(PROJ_ROOT)/nimble/host/src/ble_uuid.o \
	$(PROJ_ROOT)/nimble/host/services/ans/src/ble_svc_ans.o \
	$(PROJ_ROOT)/nimble/host/services/gap/src/ble_svc_gap.o \
	$(PROJ_ROOT)/nimble/host/services/gatt/src/ble_svc_gatt.o \
	$(PROJ_ROOT)/nimble/host/services/ias/src/ble_svc_ias.o \
	$(PROJ_ROOT)/nimble/host/services/lls/src/ble_svc_lls.o \
	$(PROJ_ROOT)/nimble/host/services/tps/src/ble_svc_tps.o \
	$(PROJ_ROOT)/nimble/host/store/ram/src/ble_store_ram.o \
	$(PROJ_ROOT)/tinycrypt/src/aes_decrypt.o \
	$(PROJ_ROOT)/tinycrypt/src/aes_encrypt.o \
	$(PROJ_ROOT)/tinycrypt/src/cmac_mode.o \
	$(PROJ_ROOT)/tinycrypt/src/ecc.o \
	$(PROJ_ROOT)/tinycrypt/src/ecc_dh.o \
	$(PROJ_ROOT)/tinycrypt/src/utils.o \

DEPS := $(OBJS:.o=.d)

CFLAGS += \
	-D NRF52 \
	-D NRF52832 \
	-D NRF52832_XXAA \
	-I $(NRF5_SDK_ROOT)/examples/peripheral/blinky_freertos/config/blinky_FreeRTOS_pca10040 \
	-I $(NRF5_SDK_ROOT)/examples/peripheral/blinky_freertos/pca10040/blank/config \
	-I $(NRF5_SDK_ROOT)/external/freertos/config \
	-I $(NRF5_SDK_ROOT)/external/freertos/portable/CMSIS/nrf52 \
	-I $(NRF5_SDK_ROOT)/external/freertos/portable/GCC/nrf52 \
	-I $(NRF5_SDK_ROOT)/external/freertos/source/include \
	-I $(NRF5_SDK_ROOT)/components/device \
	-I $(NRF5_SDK_ROOT)/components/drivers_nrf/hal \
	-I $(NRF5_SDK_ROOT)/components/drivers_nrf/nrf_soc_nosd \
	-I $(NRF5_SDK_ROOT)/components/drivers_nrf/uart \
	-I $(NRF5_SDK_ROOT)/components/libraries/util \
	-I $(NRF5_SDK_ROOT)/components/toolchain/cmsis/include \
	-I $(NRF5_SDK_ROOT)/components/toolchain/gcc \
	-I $(NRF5_SDK_ROOT)/components/toolchain \
	-I ./include \
	-I $(PROJ_ROOT)/porting/common/include \
	-I $(PROJ_ROOT)/nimble/include \
	-I $(PROJ_ROOT)/nimble/host/include \
	-I $(PROJ_ROOT)/nimble/host/mesh/include \
	-I $(PROJ_ROOT)/nimble/host/services/ans/include \
	-I $(PROJ_ROOT)/nimble/host/services/gap/include \
	-I $(PROJ_ROOT)/nimble/host/services/gatt/include \
	-I $(PROJ_ROOT)/nimble/host/services/ias/include \
	-I $(PROJ_ROOT)/nimble/host/services/lls/include \
	-I $(PROJ_ROOT)/nimble/host/services/tps/include \
	-I $(PROJ_ROOT)/nimble/host/store/ram/include \
	-I $(PROJ_ROOT)/tinycrypt/include \

CFLAGS += -mcpu=cortex-m4 -mthumb -mabi=aapcs -mfloat-abi=hard -mfpu=fpv4-sp-d16
CFLAGS += -MP -MD -Wall -Werror -Og

.PHONY: all clean

all: libnimble_nrf5_sdk.a

clean:
	rm $(OBJS) -f
	rm $(DEPS) -f
	rm libnimble_nrf5_sdk.a -f

-include $(DEPS)

libnimble_nrf5_sdk.a: $(OBJS)
	$(AR) $(ARFLAGS) $@ $^
