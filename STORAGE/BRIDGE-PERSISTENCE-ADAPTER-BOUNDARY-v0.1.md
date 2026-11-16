# AgentBridge Persistence Adapter Boundary v0.1

AgentBridge is a transport/execution integration, not the canonical storage authority.

Every bridge persistence operation must route through the DATASELF storage adapter contract. Local bridge state, pending queues, delivery receipts, webhook logs, and session caches remain operational or derived state unless individually enveloped and admitted.

The bridge adapter may:
- stage bounded operational events;
- request immutable DATASELF publication;
- verify receiver-side persistence receipts;
- recontact stored objects;
- rebuild delivery indexes from admitted event envelopes.

The bridge may not:
- overwrite canonical payload bytes;
- infer storage admission from successful message delivery;
- promote local queues into canonical memory without admission;
- claim independent custody or witness status;
- downgrade to an unadmitted backend silently.

When DATASELF is unreachable, the bridge records pending delivery and preserves the exact source bytes. It does not silently switch canonical authority.
