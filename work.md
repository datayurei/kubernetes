➜  ~ grep -oE '"(cacher\.NewCacherFromConfig|etcd3\.New)".*' /tmp/kube-apiserver.log | sort | uniq -c | sort -rn
      2 "etcd3.New" group="" resource="serviceaccounts" resourcePrefix="/serviceaccounts" calledFrom="%s:%dk8s.io/apiserver/pkg/storage/storagebackend/factory/etcd3.go482"
      2 "etcd3.New" group="" resource="events" resourcePrefix="/events" calledFrom="%s:%dk8s.io/apiserver/pkg/storage/storagebackend/factory/etcd3.go482"
      2 "cacher.NewCacherFromConfig" group="" resource="serviceaccounts" resourcePrefix="/serviceaccounts" callFrom="%s:%dk8s.io/apiserver/pkg/registry/generic/registry/storage_factory.go70"


---

I0817 01:32:05.704492  188866 store.go:149] "etcd3.New" group="" resource="serviceaccounts" resourcePrefix="/serviceaccounts" stack=<
	goroutine 1 [running]:
	runtime/debug.Stack()
		runtime/debug/stack.go:26 +0x5e
	k8s.io/apiserver/pkg/storage/etcd3.New(0x2f367a890f8, {0x3bf49c0, 0x2f367c6cea0}, {0x3c14530, 0x2f36861a480}, 0x3bc69c0, 0x3bc69c8, {0x396cabb, 0x9}, {0x2f368682c50, ...}, ...)
		k8s.io/apiserver/pkg/storage/etcd3/store.go:149 +0x67
	k8s.io/apiserver/pkg/storage/storagebackend/factory.newETCD3Storage({{{0x7ffd8c0767a8, 0x5}, {0x396cabb, 0x9}, {{0x2f367a81000, 0x1, 0x1}, {0x0, 0x0}, {0x0, ...}, ...}, ...}, ...}, ...)
		k8s.io/apiserver/pkg/storage/storagebackend/factory/etcd3.go:482 +0x456
	k8s.io/apiserver/pkg/storage/storagebackend/factory.Create({{{0x7ffd8c0767a8, 0x5}, {0x396cabb, 0x9}, {{0x2f367a81000, 0x1, 0x1}, {0x0, 0x0}, {0x0, ...}, ...}, ...}, ...}, ...)
		k8s.io/apiserver/pkg/storage/storagebackend/factory/factory.go:38 +0x17c
	k8s.io/apiserver/pkg/registry/generic.NewRawStorage(0x3c301a8?, 0x2f3680068d0?, 0x11?, {0x2f368682c50?, 0x2f368006910?})
		k8s.io/apiserver/pkg/registry/generic/storage_decorator.go:58 +0xe5
	k8s.io/apiserver/pkg/server/options.(*StorageFactoryRestOptionsFactory).GetRESTOptions.StorageWithCacher.func1(0x2f367bd8b40, {0x2f368682c50, 0x10}, 0x2f367a88f78, 0x3bc69c0, 0x3bc69c8, 0x3bc7538, 0x0, 0x0)
		k8s.io/apiserver/pkg/registry/generic/registry/storage_factory.go:47 +0x76
	k8s.io/apiserver/pkg/registry/generic/registry.(*Store).CompleteWithOptions(0x2f3688ec900, 0x2f368006d48)
		k8s.io/apiserver/pkg/registry/generic/registry/store.go:1681 +0x80f
	k8s.io/kubernetes/pkg/registry/core/serviceaccount/storage.NewREST({0x3bf0200, 0x2f36717a780}, {0x3bf0880, 0x2f3675c8de0}, {0x2f367a80ff0, 0x1, 0x1}, {0x3c15d10, 0x5fb1d40}, 0x0, ...)
		k8s.io/kubernetes/pkg/registry/core/serviceaccount/storage/storage.go:72 +0x4b2
	k8s.io/kubernetes/pkg/registry/core/rest.(*GenericConfig).NewRESTStorage(0x2f3686ca000, {0x3c224b8, 0x2f367b0d3a0}, {0x3bf0200, 0x2f36717a780})
		k8s.io/kubernetes/pkg/registry/core/rest/storage_core_generic.go:114 +0x905
	k8s.io/kubernetes/pkg/registry/core/rest.(*legacyProvider).NewRESTStorage(0x2f3686ca000, {0x3c224b8, 0x2f367b0d3a0}, {0x3bf0200, 0x2f36717a780})
		k8s.io/kubernetes/pkg/registry/core/rest/storage_core.go:160 +0x96
	k8s.io/kubernetes/pkg/controlplane/apiserver.(*Server).InstallAPIs(0x2f367625c30, {0x2f3686fe000, 0x16, 0xe?})
		k8s.io/kubernetes/pkg/controlplane/apiserver/apis.go:105 +0x1f8
	k8s.io/kubernetes/pkg/controlplane.CompletedConfig.New({0x3379000?}, {0x3c404e0, 0x2f367635c08})
		k8s.io/kubernetes/pkg/controlplane/instance.go:345 +0x1ab
	k8s.io/kubernetes/cmd/kube-apiserver/app.CreateServerChain({0x2f367549c50?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:193 +0x26e
	k8s.io/kubernetes/cmd/kube-apiserver/app.Run({0x3c225d0, 0x2f367253b80}, {0x2f367253b80?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:171 +0x385
	k8s.io/kubernetes/cmd/kube-apiserver/app.NewAPIServerCommand.func2(0x2f3672c8008, {0x2f3672c8c08?, 0x3?, 0x2d?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:118 +0x1a5
	github.com/spf13/cobra.(*Command).execute(0x2f3672c8008, {0x2f366fa4318, 0x2d, 0x2e})
		github.com/spf13/cobra@v1.10.2/command.go:1015 +0xb14
	github.com/spf13/cobra.(*Command).ExecuteC(0x2f3672c8008)
		github.com/spf13/cobra@v1.10.2/command.go:1148 +0x465
	github.com/spf13/cobra.(*Command).Execute(...)
		github.com/spf13/cobra@v1.10.2/command.go:1071
	k8s.io/component-base/cli.run(0x2f3672c8008)
		k8s.io/component-base/cli/run.go:146 +0x23e
	k8s.io/component-base/cli.Run(0x2f366f581e0?)
		k8s.io/component-base/cli/run.go:44 +0x17
	main.main()
		k8s.io/kubernetes/cmd/kube-apiserver/apiserver.go:34 +0x18
 >


 I0817 01:32:05.712420  188866 store.go:149] "etcd3.New" group="" resource="serviceaccounts" resourcePrefix="/serviceaccounts" stack=<
	goroutine 1 [running]:
	runtime/debug.Stack()
		runtime/debug/stack.go:26 +0x5e
	k8s.io/apiserver/pkg/storage/etcd3.New(0x2f368b1c9c0, {0x3bf49c0, 0x2f367c6cea0}, {0x3c14530, 0x2f36861bb40}, 0x3bc69c0, 0x3bc69c8, {0x396cabb, 0x9}, {0x2f368b98280, ...}, ...)
		k8s.io/apiserver/pkg/storage/etcd3/store.go:149 +0x67
	k8s.io/apiserver/pkg/storage/storagebackend/factory.newETCD3Storage({{{0x7ffd8c0767a8, 0x5}, {0x396cabb, 0x9}, {{0x2f367a81000, 0x1, 0x1}, {0x0, 0x0}, {0x0, ...}, ...}, ...}, ...}, ...)
		k8s.io/apiserver/pkg/storage/storagebackend/factory/etcd3.go:482 +0x456
	k8s.io/apiserver/pkg/storage/storagebackend/factory.Create({{{0x7ffd8c0767a8, 0x5}, {0x396cabb, 0x9}, {{0x2f367a81000, 0x1, 0x1}, {0x0, 0x0}, {0x0, ...}, ...}, ...}, ...}, ...)
		k8s.io/apiserver/pkg/storage/storagebackend/factory/factory.go:38 +0x17c
	k8s.io/apiserver/pkg/registry/generic.NewRawStorage(0x3c301a8?, 0x2f368006b90?, 0x11?, {0x2f368b98280?, 0x2?})
		k8s.io/apiserver/pkg/registry/generic/storage_decorator.go:58 +0xe5
	k8s.io/apiserver/pkg/server/options.(*StorageFactoryRestOptionsFactory).GetRESTOptions.StorageWithCacher.func1(0x2f3672547e0, {0x2f368b98280, 0x10}, 0x2f368b1c840, 0x3bc69c0, 0x3bc69c8, 0x3bc7538, 0x0, 0x0)
		k8s.io/apiserver/pkg/registry/generic/registry/storage_factory.go:47 +0x76
	k8s.io/apiserver/pkg/registry/generic/registry.(*Store).CompleteWithOptions(0x2f368984300, 0x2f368007008)
		k8s.io/apiserver/pkg/registry/generic/registry/store.go:1681 +0x80f
	k8s.io/kubernetes/pkg/registry/core/serviceaccount/storage.NewREST({0x3bf0200, 0x2f36717a780}, {0x3bf0880, 0x2f3675c8de0}, {0x2f367a80ff0, 0x1, 0x1}, {0x3c1d910, 0x2f3681c61c0}, 0x0, ...)
		k8s.io/kubernetes/pkg/registry/core/serviceaccount/storage/storage.go:72 +0x4b2
	k8s.io/kubernetes/pkg/registry/core/rest.(*legacyProvider).NewRESTStorage(0x2f3686ca000, {0x3c224b8, 0x2f367b0d3a0}, {0x3bf0200, 0x2f36717a780})
		k8s.io/kubernetes/pkg/registry/core/rest/storage_core.go:241 +0x21a5
	k8s.io/kubernetes/pkg/controlplane/apiserver.(*Server).InstallAPIs(0x2f367625c30, {0x2f3686fe000, 0x16, 0xe?})
		k8s.io/kubernetes/pkg/controlplane/apiserver/apis.go:105 +0x1f8
	k8s.io/kubernetes/pkg/controlplane.CompletedConfig.New({0x3379000?}, {0x3c404e0, 0x2f367635c08})
		k8s.io/kubernetes/pkg/controlplane/instance.go:345 +0x1ab
	k8s.io/kubernetes/cmd/kube-apiserver/app.CreateServerChain({0x2f367549c50?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:193 +0x26e
	k8s.io/kubernetes/cmd/kube-apiserver/app.Run({0x3c225d0, 0x2f367253b80}, {0x2f367253b80?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:171 +0x385
	k8s.io/kubernetes/cmd/kube-apiserver/app.NewAPIServerCommand.func2(0x2f3672c8008, {0x2f3672c8c08?, 0x3?, 0x2d?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:118 +0x1a5
	github.com/spf13/cobra.(*Command).execute(0x2f3672c8008, {0x2f366fa4318, 0x2d, 0x2e})
		github.com/spf13/cobra@v1.10.2/command.go:1015 +0xb14
	github.com/spf13/cobra.(*Command).ExecuteC(0x2f3672c8008)
		github.com/spf13/cobra@v1.10.2/command.go:1148 +0x465
	github.com/spf13/cobra.(*Command).Execute(...)
		github.com/spf13/cobra@v1.10.2/command.go:1071
	k8s.io/component-base/cli.run(0x2f3672c8008)
		k8s.io/component-base/cli/run.go:146 +0x23e
	k8s.io/component-base/cli.Run(0x2f366f581e0?)
		k8s.io/component-base/cli/run.go:44 +0x17
	main.main()
		k8s.io/kubernetes/cmd/kube-apiserver/apiserver.go:34 +0x18
 >


---

I0817 01:32:05.772118  188866 store.go:149] "etcd3.New" group="" resource="events" resourcePrefix="/events" stack=<
	goroutine 1 [running]:
	runtime/debug.Stack()
		runtime/debug/stack.go:26 +0x5e
	k8s.io/apiserver/pkg/storage/etcd3.New(0x2f3698a1248, {0x3bf49c0, 0x2f367c6cea0}, {0x3c14530, 0x2f3698af2a0}, 0x3bc6a08, 0x3bc6a10, {0x396cabb, 0x9}, {0x2f368ff23c8, ...}, ...)
		k8s.io/apiserver/pkg/storage/etcd3/store.go:149 +0x67
	k8s.io/apiserver/pkg/storage/storagebackend/factory.newETCD3Storage({{{0x7ffd8c0767a8, 0x5}, {0x396cabb, 0x9}, {{0x2f367a81000, 0x1, 0x1}, {0x0, 0x0}, {0x0, ...}, ...}, ...}, ...}, ...)
		k8s.io/apiserver/pkg/storage/storagebackend/factory/etcd3.go:482 +0x456
	k8s.io/apiserver/pkg/storage/storagebackend/factory.Create({{{0x7ffd8c0767a8, 0x5}, {0x396cabb, 0x9}, {{0x2f367a81000, 0x1, 0x1}, {0x0, 0x0}, {0x0, ...}, ...}, ...}, ...}, ...)
		k8s.io/apiserver/pkg/storage/storagebackend/factory/factory.go:38 +0x17c
	k8s.io/apiserver/pkg/registry/generic.NewRawStorage(...)
		k8s.io/apiserver/pkg/registry/generic/storage_decorator.go:58
	k8s.io/apiserver/pkg/registry/generic.UndecoratedStorage(0x2f368ff23c8?, {0x2f368ff23c8?, 0x2f36717a780?}, 0x3966a1d?, 0x0?, 0x3966a1d?, 0x6?, 0x3c05270?, 0x2f36a014788?)
		k8s.io/apiserver/pkg/registry/generic/storage_decorator.go:51 +0xe5
	k8s.io/apiserver/pkg/registry/generic/registry.(*Store).CompleteWithOptions(0x2f36a00d080, 0x2f368bd50e8)
		k8s.io/apiserver/pkg/registry/generic/registry/store.go:1681 +0x80f
	k8s.io/kubernetes/pkg/registry/core/event/storage.NewREST({0x3bf0200, 0x2f36717a780}, 0xe10)
		k8s.io/kubernetes/pkg/registry/core/event/storage/storage.go:55 +0x4af
	k8s.io/kubernetes/pkg/registry/events/rest.RESTStorageProvider.v1Storage({0x2f3672783f0?}, {0x3c224b8, 0x2f367b0d3a0}, {0x3bf0200, 0x2f36717a780})
		k8s.io/kubernetes/pkg/registry/events/rest/storage_events.go:55 +0x150
	k8s.io/kubernetes/pkg/registry/events/rest.RESTStorageProvider.NewRESTStorage({0x80000032723e0?}, {0x3c224b8, 0x2f367b0d3a0}, {0x3bf0200, 0x2f36717a780})
		k8s.io/kubernetes/pkg/registry/events/rest/storage_events.go:41 +0x139
	k8s.io/kubernetes/pkg/controlplane/apiserver.(*Server).InstallAPIs(0x2f367625c30, {0x2f3686fe000, 0x16, 0xe?})
		k8s.io/kubernetes/pkg/controlplane/apiserver/apis.go:105 +0x1f8
	k8s.io/kubernetes/pkg/controlplane.CompletedConfig.New({0x3379000?}, {0x3c404e0, 0x2f367635c08})
		k8s.io/kubernetes/pkg/controlplane/instance.go:345 +0x1ab
	k8s.io/kubernetes/cmd/kube-apiserver/app.CreateServerChain({0x2f367549c50?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:193 +0x26e
	k8s.io/kubernetes/cmd/kube-apiserver/app.Run({0x3c225d0, 0x2f367253b80}, {0x2f367253b80?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:171 +0x385
	k8s.io/kubernetes/cmd/kube-apiserver/app.NewAPIServerCommand.func2(0x2f3672c8008, {0x2f3672c8c08?, 0x3?, 0x2d?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:118 +0x1a5
	github.com/spf13/cobra.(*Command).execute(0x2f3672c8008, {0x2f366fa4318, 0x2d, 0x2e})
		github.com/spf13/cobra@v1.10.2/command.go:1015 +0xb14
	github.com/spf13/cobra.(*Command).ExecuteC(0x2f3672c8008)
		github.com/spf13/cobra@v1.10.2/command.go:1148 +0x465
	github.com/spf13/cobra.(*Command).Execute(...)
		github.com/spf13/cobra@v1.10.2/command.go:1071
	k8s.io/component-base/cli.run(0x2f3672c8008)
		k8s.io/component-base/cli/run.go:146 +0x23e
	k8s.io/component-base/cli.Run(0x2f366f581e0?)
		k8s.io/component-base/cli/run.go:44 +0x17
	main.main()
		k8s.io/kubernetes/cmd/kube-apiserver/apiserver.go:34 +0x18
 >


I0817 01:32:05.699022  188866 store.go:149] "etcd3.New" group="" resource="events" resourcePrefix="/events" stack=<
	goroutine 1 [running]:
	runtime/debug.Stack()
		runtime/debug/stack.go:26 +0x5e
	k8s.io/apiserver/pkg/storage/etcd3.New(0x2f367a88cc0, {0x3bf49c0, 0x2f367c6cea0}, {0x3c14530, 0x2f368699500}, 0x3bc6a08, 0x3bc6a10, {0x396cabb, 0x9}, {0x2f368682978, ...}, ...)
		k8s.io/apiserver/pkg/storage/etcd3/store.go:149 +0x67
	k8s.io/apiserver/pkg/storage/storagebackend/factory.newETCD3Storage({{{0x7ffd8c0767a8, 0x5}, {0x396cabb, 0x9}, {{0x2f367a81000, 0x1, 0x1}, {0x0, 0x0}, {0x0, ...}, ...}, ...}, ...}, ...)
		k8s.io/apiserver/pkg/storage/storagebackend/factory/etcd3.go:482 +0x456
	k8s.io/apiserver/pkg/storage/storagebackend/factory.Create({{{0x7ffd8c0767a8, 0x5}, {0x396cabb, 0x9}, {{0x2f367a81000, 0x1, 0x1}, {0x0, 0x0}, {0x0, ...}, ...}, ...}, ...}, ...)
		k8s.io/apiserver/pkg/storage/storagebackend/factory/factory.go:38 +0x17c
	k8s.io/apiserver/pkg/registry/generic.NewRawStorage(...)
		k8s.io/apiserver/pkg/registry/generic/storage_decorator.go:58
	k8s.io/apiserver/pkg/registry/generic.UndecoratedStorage(0x2f368682978?, {0x2f368682978?, 0x2f36717a780?}, 0x3966a1d?, 0x0?, 0x3966a1d?, 0x6?, 0x3c05270?, 0x2f3686e1408?)
		k8s.io/apiserver/pkg/registry/generic/storage_decorator.go:51 +0xe5
	k8s.io/apiserver/pkg/registry/generic/registry.(*Store).CompleteWithOptions(0x2f3686ccc00, 0x2f368006d60)
		k8s.io/apiserver/pkg/registry/generic/registry/store.go:1681 +0x80f
	k8s.io/kubernetes/pkg/registry/core/event/storage.NewREST({0x3bf0200, 0x2f36717a780}, 0xe10)
		k8s.io/kubernetes/pkg/registry/core/event/storage/storage.go:55 +0x4af
	k8s.io/kubernetes/pkg/registry/core/rest.(*GenericConfig).NewRESTStorage(0x2f3686ca000, {0x3c224b8, 0x2f367b0d3a0}, {0x3bf0200, 0x2f36717a780})
		k8s.io/kubernetes/pkg/registry/core/rest/storage_core_generic.go:88 +0x6ea
	k8s.io/kubernetes/pkg/registry/core/rest.(*legacyProvider).NewRESTStorage(0x2f3686ca000, {0x3c224b8, 0x2f367b0d3a0}, {0x3bf0200, 0x2f36717a780})
		k8s.io/kubernetes/pkg/registry/core/rest/storage_core.go:160 +0x96
	k8s.io/kubernetes/pkg/controlplane/apiserver.(*Server).InstallAPIs(0x2f367625c30, {0x2f3686fe000, 0x16, 0xe?})
		k8s.io/kubernetes/pkg/controlplane/apiserver/apis.go:105 +0x1f8
	k8s.io/kubernetes/pkg/controlplane.CompletedConfig.New({0x3379000?}, {0x3c404e0, 0x2f367635c08})
		k8s.io/kubernetes/pkg/controlplane/instance.go:345 +0x1ab
	k8s.io/kubernetes/cmd/kube-apiserver/app.CreateServerChain({0x2f367549c50?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:193 +0x26e
	k8s.io/kubernetes/cmd/kube-apiserver/app.Run({0x3c225d0, 0x2f367253b80}, {0x2f367253b80?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:171 +0x385
	k8s.io/kubernetes/cmd/kube-apiserver/app.NewAPIServerCommand.func2(0x2f3672c8008, {0x2f3672c8c08?, 0x3?, 0x2d?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:118 +0x1a5
	github.com/spf13/cobra.(*Command).execute(0x2f3672c8008, {0x2f366fa4318, 0x2d, 0x2e})
		github.com/spf13/cobra@v1.10.2/command.go:1015 +0xb14
	github.com/spf13/cobra.(*Command).ExecuteC(0x2f3672c8008)
		github.com/spf13/cobra@v1.10.2/command.go:1148 +0x465
	github.com/spf13/cobra.(*Command).Execute(...)
		github.com/spf13/cobra@v1.10.2/command.go:1071
	k8s.io/component-base/cli.run(0x2f3672c8008)
		k8s.io/component-base/cli/run.go:146 +0x23e
	k8s.io/component-base/cli.Run(0x2f366f581e0?)
		k8s.io/component-base/cli/run.go:44 +0x17
	main.main()
		k8s.io/kubernetes/cmd/kube-apiserver/apiserver.go:34 +0x18
 >

---

I0817 01:32:05.704610  188866 cacher.go:353] "cacher.NewCacherFromConfig" group="" resource="serviceaccounts" resourcePrefix="/serviceaccounts" stack=<
	goroutine 1 [running]:
	runtime/debug.Stack()
		runtime/debug/stack.go:26 +0x5e
	k8s.io/apiserver/pkg/storage/cacher.NewCacherFromConfig({{0x3c4e180, 0x2f3688f4d20}, {0x3c2bbc0, 0x5fb1d40}, {{0x0, 0x0}, {0x3978fec, 0xf}}, 0x1176592e00, {0x2f368682c50, ...}, ...})
		k8s.io/apiserver/pkg/storage/cacher/cacher.go:353 +0x25
	k8s.io/apiserver/pkg/server/options.(*StorageFactoryRestOptionsFactory).GetRESTOptions.StorageWithCacher.func1(0x2f367bd8b40, {0x2f368682c50, 0x10}, 0x2f367a88f78, 0x3bc69c0, 0x3bc69c8, 0x3bc7538, 0x0, 0x0)
		k8s.io/apiserver/pkg/registry/generic/registry/storage_factory.go:70 +0x2f5
	k8s.io/apiserver/pkg/registry/generic/registry.(*Store).CompleteWithOptions(0x2f3688ec900, 0x2f368006d48)
		k8s.io/apiserver/pkg/registry/generic/registry/store.go:1681 +0x80f
	k8s.io/kubernetes/pkg/registry/core/serviceaccount/storage.NewREST({0x3bf0200, 0x2f36717a780}, {0x3bf0880, 0x2f3675c8de0}, {0x2f367a80ff0, 0x1, 0x1}, {0x3c15d10, 0x5fb1d40}, 0x0, ...)
		k8s.io/kubernetes/pkg/registry/core/serviceaccount/storage/storage.go:72 +0x4b2
	k8s.io/kubernetes/pkg/registry/core/rest.(*GenericConfig).NewRESTStorage(0x2f3686ca000, {0x3c224b8, 0x2f367b0d3a0}, {0x3bf0200, 0x2f36717a780})
		k8s.io/kubernetes/pkg/registry/core/rest/storage_core_generic.go:114 +0x905
	k8s.io/kubernetes/pkg/registry/core/rest.(*legacyProvider).NewRESTStorage(0x2f3686ca000, {0x3c224b8, 0x2f367b0d3a0}, {0x3bf0200, 0x2f36717a780})
		k8s.io/kubernetes/pkg/registry/core/rest/storage_core.go:160 +0x96
	k8s.io/kubernetes/pkg/controlplane/apiserver.(*Server).InstallAPIs(0x2f367625c30, {0x2f3686fe000, 0x16, 0xe?})
		k8s.io/kubernetes/pkg/controlplane/apiserver/apis.go:105 +0x1f8
	k8s.io/kubernetes/pkg/controlplane.CompletedConfig.New({0x3379000?}, {0x3c404e0, 0x2f367635c08})
		k8s.io/kubernetes/pkg/controlplane/instance.go:345 +0x1ab
	k8s.io/kubernetes/cmd/kube-apiserver/app.CreateServerChain({0x2f367549c50?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:193 +0x26e
	k8s.io/kubernetes/cmd/kube-apiserver/app.Run({0x3c225d0, 0x2f367253b80}, {0x2f367253b80?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:171 +0x385
	k8s.io/kubernetes/cmd/kube-apiserver/app.NewAPIServerCommand.func2(0x2f3672c8008, {0x2f3672c8c08?, 0x3?, 0x2d?})
		k8s.io/kubernetes/cmd/kube-apiserver/app/server.go:118 +0x1a5
	github.com/spf13/cobra.(*Command).execute(0x2f3672c8008, {0x2f366fa4318, 0x2d, 0x2e})
		github.com/spf13/cobra@v1.10.2/command.go:1015 +0xb14
	github.com/spf13/cobra.(*Command).ExecuteC(0x2f3672c8008)
		github.com/spf13/cobra@v1.10.2/command.go:1148 +0x465
	github.com/spf13/cobra.(*Command).Execute(...)
		github.com/spf13/cobra@v1.10.2/command.go:1071
	k8s.io/component-base/cli.run(0x2f3672c8008)
		k8s.io/component-base/cli/run.go:146 +0x23e
	k8s.io/component-base/cli.Run(0x2f366f581e0?)
		k8s.io/component-base/cli/run.go:44 +0x17
	main.main()
		k8s.io/kubernetes/cmd/kube-apiserver/apiserver.go:34 +0x18
 >

