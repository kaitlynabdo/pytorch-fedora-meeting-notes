**Meeting Summary 7/24/23**



1. **Agenda**
    1. Discuss package dependency search
    2. Discuss what information we’re still looking for
2. **Discussion Summary**
    3. We are not packaging for Cuda
    4. Version requirements
        1. Question was asked about which version of python we’ll be using, this lead to a larger conversation about version requirements 
        2. Action item was created to add versions for the list of required packages
    5. First release, plan is to focus on AMD ROCm first
        3. oneAPI was discussed but due to ROCm code base being further along and more robust, oneAPI will not be a priority for this release
    6. Concerns about LLVM packages due to patches upstream and licensing issues were discussed since there might be some packages required for PyTorch that are included in that
3. **Action Items/Questions to Think About**
    7. Compile a list of package versions along with the remaining package list
    8. Determine what packages have already been packaged for fedora
        4. [https://src.fedoraproject.org/](https://src.fedoraproject.org/)
    9. Determine if any packages are for LLVM
    10. Are we shipping this as one large package or a couple of packages?
4. **Resources**
    11. Any discussion or updates will be hosted on this [discussion](https://discussion.fedoraproject.org/t/pytorch-packages-and-dependencies-7-17/85952), the same topic on Fedora Discussion from last week
    12. A [spreadsheet](https://docs.google.com/spreadsheets/d/1MunNWKjhhT_sBQUueKsRcz_qZVp9ZLwErq10PyN34AY/edit?usp=sharing) to keep track of pytorch dependencies and versions
    13. Additional notes are for everyone to post notes, resources, etc. 

**Additional Notes**

_This section is for everyone to post and share what they come across/come up with. _

To get a quick list I used below. I’m sure it’s imperfect, but should at least provide a decent starting place.

for i in pkgconf ca-certificates-mozilla berkeley-db libiconv zlib gmake libmd xz zstd libffi re2c libsigsegv findutils util-macros libunwind libpthread-stubs xxd-standalone roctracer-dev-api pcre2 half libyaml chrpath ncurses util-linux-uuid nghttp2 libunistring diffutils pigz libbsd libxml2 kbproto xproto glproto inputproto renderproto xextproto randrproto xtrans readline libedit libidn2 bzip2 m4 expat libxau libxdmcp libice sqlite gdbm boost tar libtool libsm perl gettext libpciaccess perl-module-build openssl autoconf libxcrypt perl-file-which elfutils bison hwloc perl-uri-encode libevent curl automake python krb5 flex pmix cmake numactl xcb-proto python3-pip ninja openssh eigen msgpack-c nlohmann-json intel-tbb protobuf z3 rocm-cmake rocm-smi-lib libxcb python3-wheel python3-setuptools fxdiv psimd pthreadpool git openmpi intel-oneapi-mkl llvm-amdgpu libx11 python3-flit-core python3-protobuf python3-editables python3-charset-normalizer python3-calver python3-networkx python3-pybind11 meson python3-certifi python3-cython python3-distlib python3-urllib3 python3-ply python3-six python3-markupsafe valgrind libxrender libxext libxt python3-pathspec python3-idna python3-tomli python3-typing-extensions python3-packaging python3-trove-classifiers libdrm python3-numpy python3-msgpack python3-pyyaml python3-cppheaderparser python3-astunparse python3-mako python3-jinja2 libxrandr python3-requests python3-setuptools-scm hsakmt-roct xrandr python3-mpmath python3-pluggy python3-tqdm python3-sympy python3-hatchling python3-hatch-vcs python3-platformdirs python3-filelock python3-virtualenv; do echo $i  $(sudo dnf list available --showduplicates | grep -e x86_64 -e noarch | grep -w ^$i | head -n 1 | awk -F ' ' '{ print $1 " " $2 }' ); done
