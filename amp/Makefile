BUNDLE = amp.lv2
INSTALL_DIR = /usr/local/lib/lv2

$(BUNDLE): manifest.ttl amp.ttl amp.so
	rm -rf $(BUNDLE)
	mkdir $(BUNDLE)
	cp manifest.ttl amp.ttl amp.so $(BUNDLE)

amp.so: amp.c
	gcc -shared -fPIC -DPIC amp.c `pkg-config --cflags --libs lv2` -o amp.so

install: $(BUNDLE)
	mkdir -p $(INSTALL_DIR)
	rm -rf $(INSTALL_DIR)/$(BUNDLE)
	cp -R $(BUNDLE) $(INSTALL_DIR)

clean:
	rm -rf $(BUNDLE) amp.so
