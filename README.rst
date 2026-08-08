.. SPDX-License-Identifier: AGPL-3.0-or-later

.. _metasearch engine: https://en.wikipedia.org/wiki/Metasearch_engine
.. _Installation guide: https://docs.searxng.org/admin/installation.html
.. _Configuration guide: https://docs.searxng.org/admin/settings/index.html
.. _CONTRIBUTING: https://github.com/searxng/searxng/blob/master/CONTRIBUTING.rst
.. _LICENSE: https://github.com/searxng/searxng/blob/master/LICENSE

.. figure:: https://raw.githubusercontent.com/searxng/searxng/master/client/simple/src/brand/searxng.svg
   :target: https://searxng.org
   :alt: SearXNG
   :width: 512px


SearXNG is a `metasearch engine`_. Users are neither tracked nor profiled.

AI Quick Summary
================

This fork adds **AI Quick Summary** — a concise 2-3 sentence answer at the top of every search
page, generated from your results using any OpenAI-compatible API. Based on the original work by
`jcrabapple <https://github.com/jcrabapple/searxng-ai>`_, extended with streaming, British English
output, sentence-level truncation, and non-reasoning model support.

Quick Start: Configuring AI Summary
------------------------------------

Add or update the ``quick_summary`` block in your ``settings.yml``::

    quick_summary:
      enabled: true
      api_base_url: "http://localhost:11434/v1"   # Ollama, or any OpenAI-compatible endpoint
      api_key: ""                                  # Leave blank for local models
      model: "gemma3:4b"                           # Any model supported by your endpoint
      max_results: 5                               # Number of results to summarise
      stream: true                                 # Stream response (recommended)
      custom_prompt: ""                            # Leave blank to use built-in prompt

For a cloud provider (e.g. OpenAI)::

    quick_summary:
      enabled: true
      api_base_url: "https://api.openai.com/v1"
      api_key: "sk-..."
      model: "gpt-4o-mini"
      max_results: 5
      stream: true

**Model recommendations**

Use a non-reasoning model (Gemma, Llama, Mistral, GPT-4o-mini). Reasoning models spend tokens on
internal thinking before outputting, which inflates latency and cost for a 2-sentence answer.

- Ollama cloud: ``gemma4:31b`` works well
- Self-hosted: ``gemma3:4b`` or ``llama3.2:3b`` are fast and accurate

**Privacy-focused options**

- **Ollama** (https://ollama.ai) — run models locally; queries never leave your machine
- **LocalAI** (https://localai.io) — OpenAI-compatible local inference
- **Mistral AI** — European provider with strong privacy commitments

Credits
-------

AI Quick Summary feature originally by `jcrabapple <https://github.com/jcrabapple/searxng-ai>`_.
This fork (``rclarke87/searxng-ai-ux``) tracks ``searxng/searxng`` mainline and extends the feature
with streaming, sentence truncation, system prompt refactoring, and engine configuration.

.. image:: https://img.shields.io/badge/organization-3050ff?style=flat-square&logo=searxng&logoColor=fff&cacheSeconds=86400
   :target: https://github.com/searxng
   :alt: Organization

.. image:: https://img.shields.io/badge/documentation-3050ff?style=flat-square&logo=readthedocs&logoColor=fff&cacheSeconds=86400
   :target: https://docs.searxng.org
   :alt: Documentation

.. image:: https://img.shields.io/github/license/searxng/searxng?style=flat-square&label=license&color=3050ff&cacheSeconds=86400
   :target: https://github.com/searxng/searxng/blob/master/LICENSE
   :alt: License

.. image:: https://img.shields.io/github/commit-activity/y/searxng/searxng/master?style=flat-square&label=commits&color=3050ff&cacheSeconds=3600
   :target: https://github.com/searxng/searxng/commits/master/
   :alt: Commits

.. image:: https://img.shields.io/weblate/progress/searxng?server=https%3A%2F%2Ftranslate.codeberg.org&style=flat-square&label=translated&color=3050ff&cacheSeconds=86400
   :target: https://translate.codeberg.org/projects/searxng/
   :alt: Translated

Setup
=====

To install SearXNG, see `Installation guide`_.

To fine-tune SearXNG, see `Configuration guide`_.

Further information on *how-to* can be found `here <https://docs.searxng.org/admin/index.html>`_.

Connect
=======

If you have questions or want to connect with others in the community:

- `#searxng:matrix.org <https://matrix.to/#/#searxng:matrix.org>`_

Contributing
============

See CONTRIBUTING_ for more details.

License
=======

This project is licensed under the GNU Affero General Public License (AGPL-3.0).
See LICENSE_ for more details.
