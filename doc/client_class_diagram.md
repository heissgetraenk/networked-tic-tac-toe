```mermaid
classDiagram

class RenderingEngine

class State
class Transition
class StateMachine

class Socket
class AbstractInput
class TcpInput
class AbstractOutput
class TcpOutput

StateMachine o-- State
StateMachine o-- Transition

Socket <|-- AbstractInput
Socket <|-- AbstractOutput
AbstractInput <|-- TcpInput
AbstractOutput <|-- TcpOutput
StateMachine o-- Socket
StateMachine --> RenderingEngine

```